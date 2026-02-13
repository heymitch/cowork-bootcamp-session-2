---
name: voice-memo-to-post
description: Turn voice memos, rough notes, and raw ideas into publish-ready social media posts — researched, hooked, and saved to Notion. Say "Turn this into a post" or "Post this to LinkedIn".
---

# Voice Memo to Post

## What This Does

Takes your raw input — voice memo, rough notes, a topic, a half-baked idea — and turns it into a publish-ready post. Picks the right hook framework, researches context if needed, writes in your voice, and saves to Notion.

## How to Run

- "Turn this voice memo into a post" + drop the audio file
- "Polish these rough notes: [paste notes]"
- "I rambled about [topic] — make it a LinkedIn post"
- "Post this idea: [raw thought]"

---

## Preflight Check (Run Silently)

### 1. Config check
Read `config.md` from project root.
- **Missing:** Stop. Say: "Say **'Run my business blueprint'** first — takes 5 minutes."
- **Exists:** Continue.

### 2. Voice check
Check config.md for `- [x] Voice Training completed`.
- **Unchecked:** Stop. Say: "Say **'Train on my voice'** first so this sounds like you."
- **Checked:** Load Voice Profile. Wrap all content generation with `<VOICE>{profile}</VOICE>`.

### 3. Notion check (silent)
- **Notion tools found:** Will save to Notion. Update checkbox if unchecked.
- **No Notion tools:** Save locally. Don't mention Notion.

### 4. All clear — proceed without announcing.

---

## The Process

### Step 1: Capture the Raw Input
If audio file → transcribe it. If text → read it. If topic only → use it as the seed.
Show the raw transcription/notes back to the user so they can see what you're working with.

### Step 2: Extract the Core Idea
What's the one thing they're saying? Distill to a single sentence. If the input has multiple ideas, pick the strongest and mention the others: "I see 3 ideas here — going with [strongest]. Want me to draft the others after?"

### Step 3: Research (If Needed)
If the core idea references a trend, news event, stat, or claim that needs context:
- Use web search to find current supporting info
- Add one data point or fact to strengthen the post
- Never fabricate. If search returns nothing useful, write without it
Skip research for personal stories, opinions, or experience-based posts.

### Step 4: Pick the Hook Framework
Read the raw input energy and select from the 5 frameworks in `references/hook-frameworks.md`:
- Frustration/disagreement → **Contrarian** or **Hot Take**
- "Let me tell you what happened" → **Personal Story**
- Curiosity/wondering → **Question**
- "I see where this is going" → **Prediction**
If unclear, present top 2 with sample hooks and let user choose.

### Step 5: Pick the Platform
If user didn't specify, match to content:
- Short + punchy → X single (≤280 chars)
- Story or lesson with depth → LinkedIn (800-1200 chars)
- Multiple connected points → X thread or LinkedIn (ask)
Confirm: "This feels like a LinkedIn post — want it there or somewhere else?"
See `references/post-structure.md` for platform formats.

### Step 6: Write the Draft
Using hook framework + platform format + voice profile:
- Apply `<VOICE>{Voice Template}</VOICE>` wrapper
- Preserve the user's original phrasing where it's strong
- Structure: Hook → Body → CTA
- Never add ideas that weren't in the original (research context is the exception)

### Step 7: Show Original + Draft
Present side by side with hook framework labeled and character count.
**Do not save yet.** Wait for approval or edits.

### Step 8: Save to Notion
On approval: save to Notion content database (or local `content/YYYY-MM/DD-[slug].md`).
Include frontmatter: platform, date, status (draft), hook_framework used.

## Input Formats

Audio files (.m4a, .mp3, .wav, .ogg), rough text, file paths, Notion pages, or just a topic.

## Rules

- Always show original alongside draft so user can compare.
- Preserve unique phrases, strong opinions, personal stories, specific examples.
- Remove filler, repetition, tangents. Add structure and platform formatting.
- If the input is too short for a full post, ask for one clarifying detail — don't pad.
- Human writing rules: no AI patterns, vary sentence length, specific > vague.
