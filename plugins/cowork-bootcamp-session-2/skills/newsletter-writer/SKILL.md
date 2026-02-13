---
name: newsletter-writer
description: Draft your weekly newsletter — from idea to finished draft with subject lines — in your voice. Say "Write my newsletter" or "Draft a newsletter about [topic]".
---

# Newsletter Writer

## What This Does

Takes you from a vague idea to a polished newsletter draft in ~11 minutes. Runs a clarity exercise, picks a template, writes in your voice, generates subject lines with preview-text. You review, tweak, publish.

## How to Run

- "Write my newsletter for this week"
- "Draft a newsletter about [topic]"
- "Newsletter from my notes this week"

---

## Preflight Check (Run Silently)

### 1. Config check
Read `config.md` from project root.
- **Missing:** Stop. Say: "Say **'Run my business blueprint'** first — takes 5 minutes."
- **Exists:** Continue.

### 2. Voice check
Check config.md for `- [x] Voice Training completed`.
- **Unchecked:** Stop. Say: "Say **'Train on my voice'** first so this sounds like you."
- **Checked:** Load Voice Profile section. Wrap all content generation with `<VOICE>{profile}</VOICE>`.

### 3. Notion check (silent)
- **Notion tools found:** Will save to Notion. Update checkbox if unchecked.
- **No Notion tools:** Save locally. Don't mention Notion.

### 4. All clear — proceed without announcing.

---

## The Process

### Step 1: Find Material
If Notion connected, scan recent notes/highlights/ideas from the past 7 days. If not, ask: "What do you want to write about this week? Drop a topic, paste some notes, or point me to a file."

### Step 2: Pinpoint Writing
Run the 5-question clarity exercise from `references/pinpoint-writing.md`. This locks in the angle before writing a single word. For repeat users with a clear topic, infer answers from context and confirm.

### Step 3: Pick the Format
Ask: "Curating resources for your readers, or sharing your own thinking?" See `references/newsletter-templates.md` for the two newsletter types and body templates. Default to Original Thinking for most creators.

### Step 4: Build the Headline
Generate 3-5 headline options using the Irresistible Headlines formula from `references/headline-formula.md`. Present with pieces labeled. User picks or combines.

### Step 5: Write the Draft
Using the chosen template + headline + Pinpoint Writing answers + voice profile:
- Write the full newsletter body
- Apply the `<VOICE>{Voice Template}</VOICE>` wrapper from config.md
- Follow the template structure exactly — don't skip sections

### Step 6: Generate Subject Lines
After the draft is written, generate 4 subject line + preview-text pairs using `references/subject-lines.md`. One for each hook type, each with a matching whisper.

### Step 7: Show Everything
Present the draft + subject line options. **Do not save yet.** Wait for approval or edits.

### Step 8: Save
On approval: save to Notion (if connected) or local markdown file. Suggest 3 social media hooks to promote the newsletter.

## Customization

- **Change the source.** Point at specific Notion databases instead of scanning everything.
- **Change the format.** Describe newsletter sections in config.md for custom structure.
- **Change the frequency.** Weekly, biweekly, or daily digest.

## Rules

- Always show the draft before saving. Never publish directly.
- Use the voice profile. If the draft sounds generic, you skipped the voice wrapper.
- If no notes and no topic, ask. Do not fabricate.
- Human writing rules: no AI-tell patterns, vary sentence length, use specific details over vague claims.
- Subject lines: 9 words max, 60 characters max, sentence case, visceral language.
- After first successful run, update config.md Setup Status.
