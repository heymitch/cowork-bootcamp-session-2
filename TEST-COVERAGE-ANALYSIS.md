# Test Coverage Analysis — Cowork Bootcamp Session 2

## How Testing Works for Cowork Plugins

Cowork plugins are tested natively using Claude Code's `--plugin-dir` flag, which loads the plugin locally for manual skill invocation and validation. There are no automated test frameworks — testing is done by invoking skills and verifying outputs match expected behavior.

```bash
claude --plugin-dir ./plugins/cowork-bootcamp-session-2
```

Then invoke skills with their trigger phrases or namespaced commands to verify behavior.

---

## Current Test Coverage

### What's Tested Today

| Component | Test Type | Location | What It Validates |
|-----------|-----------|----------|-------------------|
| **Voice Training** | Mimic & Modify (Step 9) | `voice-training/SKILL.md:81-82` | Rewrites a generic paragraph using the voice profile, asks "Does this sound like you?" |
| **Notion Connector** | Manual smoke test | `notion-connector/SKILL.md:26-38` | Two manual checks: list pages, create a test page |
| **Newsletter Writer** | Approval gate | `newsletter-writer/SKILL.md:63-64` | Shows draft before saving — but no structured test |
| **Voice Memo to Post** | Approval gate | `voice-memo-to-post/SKILL.md:80-82` | Shows original + draft side-by-side — but no structured test |
| **Voice Stacking** | Rule only | `voice-stacking.md:80` | "Never skip the Avoid Words" — rule exists but no explicit test step |

### What's Not Tested

| Gap | Risk | Severity |
|-----|------|----------|
| Preflight checks (all 3 skills) | Skills may proceed without config.md or voice profile, producing generic output | High |
| Skill trigger recognition | Wrong skill may activate, or skill may not activate at all | Medium |
| Cross-skill voice consistency | Voice profile may not transfer correctly between voice-training → newsletter-writer → voice-memo-to-post | High |
| Newsletter Writer end-to-end | No "test it" section like Notion connector has | High |
| Voice Memo to Post end-to-end | No "test it" section like Notion connector has | High |
| Subject line format rules | Rules say "9 words max, 60 characters max" but no validation step confirms this | Medium |
| Headline formula completeness | 5-piece formula outputs aren't checked against the formula | Medium |
| Avoid Words enforcement | Rule says to check output against avoid list, but no test verifies this happens | High |
| Platform format compliance | Post structure rules (LinkedIn 800-1200 chars, X ≤280) aren't validated | Medium |
| Error paths and edge cases | What happens with malformed config.md, incomplete voice profile, empty writing samples | Medium |
| Notion save verification | Approval gate exists but no test confirms content actually saved correctly | Low |

---

## Proposed Improvements

### 1. Add "Test It" Sections to Newsletter Writer and Voice Memo to Post

**Problem:** The Notion Connector has a clear "Test It" section that walks users through verifying the connection works. Neither of the two writing skills have an equivalent.

**Proposal:** Add a `## Test It` section to each skill's `SKILL.md` with a concrete smoke test:

**Newsletter Writer — proposed test:**
```markdown
## Test It

After Voice Training is complete, try:

> "Write my newsletter about why most people overthink their first post"

The agent should:
1. Run the Pinpoint Writing exercise (5 questions)
2. Present 3-5 headline options with formula pieces labeled
3. Write a full draft in your voice (not generic AI voice)
4. Generate 4 subject line + preview-text pairs
5. Wait for your approval before saving

If the draft sounds like you (not like ChatGPT), the skill is working.
```

**Voice Memo to Post — proposed test:**
```markdown
## Test It

After Voice Training is complete, try:

> "Turn this into a post: I realized today that the best meetings
> are the ones where someone says 'we don't need this meeting.'
> Most meetings exist to make people feel busy."

The agent should:
1. Extract the core idea (unnecessary meetings)
2. Pick a hook framework (likely Contrarian or Hot Take)
3. Suggest a platform (likely LinkedIn)
4. Show original alongside the draft with character count
5. Wait for approval

If the hook is sharp and the voice matches yours, the skill is working.
```

---

### 2. Add Preflight Check Verification Tests

**Problem:** Each skill runs silent preflight checks (config.md exists, voice training completed, Notion connected), but there's no way to verify these gates actually stop execution when they should.

**Proposal:** Add a `## Verify Preflight Checks` section to the README or a new `TESTING.md` with explicit negative tests:

```markdown
## Verify Preflight Checks

Test each skill WITHOUT completing the prerequisites:

### Test 1: No config.md
Delete or rename config.md. Run "Write my newsletter."
Expected: Agent stops and says "Say 'Run my business blueprint' first."

### Test 2: No Voice Training
Ensure config.md exists but voice training is unchecked.
Run "Write my newsletter."
Expected: Agent stops and says "Say 'Train on my voice' first."

### Test 3: Voice Training present
Complete voice training. Run "Write my newsletter."
Expected: Agent proceeds to Pinpoint Writing without mentioning prerequisites.
```

---

### 3. Add Voice Consistency Cross-Skill Test

**Problem:** The voice stacking pattern (`<VOICE>{profile}</VOICE>`) is the core mechanism linking voice-training output to all writing skills. If the voice template format changes or a skill fails to load it, output reverts to generic AI writing. There's no test that validates this chain.

**Proposal:** Add a cross-skill integration test:

```markdown
## Voice Consistency Test

1. Complete Voice Training with your samples
2. Note 2-3 of your Power Words and 2-3 Avoid Words from the profile
3. Run "Write my newsletter about [any topic]"
4. Run "Turn this into a post: [any raw idea]"

For both outputs, check:
- [ ] At least 1 Power Word appears naturally
- [ ] Zero Avoid Words appear
- [ ] Tone matches your Tone Grid placement (loose vs tight, irreverent vs professional)
- [ ] Archetype mix is reflected (e.g., if you're 50% Frameworker, the output has structure)
- [ ] Output does NOT contain AI-tell words: "delve", "landscape", "game-changer", "supercharge", "crucial"
```

---

### 4. Add Output Format Validation Rules to Skill Instructions

**Problem:** The reference docs define specific format constraints (subject lines: 9 words max / 60 chars max; LinkedIn posts: 800-1200 chars; X posts: ≤280 chars) but the skill instructions don't include a self-check step that validates these constraints before showing output to the user.

**Proposal:** Add a validation step before the "Show Everything" step in each skill:

**Newsletter Writer — add before Step 7:**
```markdown
### Step 6b: Validate Output
Before showing the draft, silently verify:
- Each subject line is ≤9 words and ≤60 characters
- Each subject line uses sentence case (not Title Case)
- Preview-text complements (doesn't repeat) the subject line
- The draft follows the chosen template structure completely
- No Avoid Words from the voice profile appear in the draft
If any check fails, fix it before presenting.
```

**Voice Memo to Post — add before Step 7:**
```markdown
### Step 6b: Validate Output
Before showing the draft, silently verify:
- Character count is within platform limits (LinkedIn: 800-1200, X: ≤280, Thread: ≤280/tweet)
- Hook framework is correctly applied (opening matches the pattern)
- No Avoid Words from the voice profile appear
- Original phrasing is preserved where it was strong
If any check fails, fix it before presenting.
```

---

### 5. Add Headline Formula Completeness Check

**Problem:** The Irresistible Headlines formula defines 5 pieces (How Many, The Who, The What, The Why, Twist the Knife). The skill says "generate 3-5 headline options" but doesn't verify that each option uses enough pieces to be effective.

**Proposal:** Add to the newsletter-writer skill after headline generation:

```markdown
For each headline option, label the formula pieces used:
| Piece | Present? | Value |
|-------|----------|-------|
| HOW MANY | ✓/✗ | [value] |
| THE WHO | ✓/✗ | [value] |
| THE WHAT | ✓/✗ | [value] |
| THE WHY | ✓/✗ | [value] |
| TWIST | ✓/✗ | [value] |

Each headline should use at least 3 of 5 pieces. If any headline uses fewer than 3, strengthen it before presenting.
```

---

### 6. Add Notion Connector Error Path Tests

**Problem:** The Notion connector's "Test It" section only covers the happy path. The troubleshooting table lists 3 common problems but doesn't provide test steps to reproduce them.

**Proposal:** Expand the Test It section:

```markdown
## Test Error Handling

### Test: Unshared page
Create a new Notion page but do NOT share it with the integration.
Ask: "Read my page called [page name]"
Expected: Agent explains the page isn't shared and points to Step 3 of setup.

### Test: Invalid API key
Temporarily change the API key to an invalid value.
Ask: "List my Notion pages"
Expected: Agent reports connection failure and suggests re-checking the API key.
```

---

## Priority Order

Based on risk and effort:

| Priority | Improvement | Effort | Impact |
|----------|-------------|--------|--------|
| **1** | Add "Test It" to Newsletter Writer and Voice Memo to Post (#1) | Low | High — these are the most-used skills with zero smoke tests |
| **2** | Add output format validation steps (#4) | Low | High — prevents broken subject lines and over-length posts |
| **3** | Add voice consistency cross-skill test (#3) | Low | High — validates the core value proposition of the plugin |
| **4** | Add preflight check verification (#2) | Low | Medium — ensures prerequisite gates work |
| **5** | Add headline formula completeness check (#5) | Low | Medium — improves headline quality |
| **6** | Add Notion error path tests (#6) | Low | Low — edge cases for optional connector |

All proposed changes are documentation-only (edits to existing `.md` files or a new `TESTING.md`). No code changes required.
