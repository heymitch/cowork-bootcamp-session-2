---
name: newsletter-writer
description: Draft your weekly newsletter by pulling from your Notion notes, writing in your voice, and saving the finished draft. Say "Write my newsletter" or "Draft a newsletter about [topic]".
---

# Newsletter Writer

## What This Does

Writes your newsletter. Scans your recent notes for ideas, writes a draft in your voice, and saves it. You review, tweak, publish.

## How to Run

- "Write my newsletter for this week"
- "Draft a newsletter about [topic]"
- "Newsletter from my notes this week"

---

## Preflight Check (Run Every Time)

Before writing anything, run through this checklist silently. Only speak up if something is missing.

### 1. Does config.md exist?

Read `config.md` from the project root.

- **If missing:** Stop. Say:
  > "I need to know about you and your business first. Say **'Run my business blueprint'** — it takes 5 minutes and makes everything I write actually sound like you."
- **If exists:** Continue. Read the Setup Status section.

### 2. Is Voice Training complete?

Check config.md for `- [x] Voice Training completed` in the Setup Status section.

- **If unchecked or missing:** Stop. Say:
  > "I can write a newsletter, but it won't sound like you yet. Say **'Train on my voice'** first — it takes a few minutes and I only need to do it once. Then come back and say 'Write my newsletter' again."
- **If checked:** Continue. Load the Voice Samples section from config.md.

### 3. Is Notion connected?

Check your available tools for Notion tools (search, create page, read page, etc.).

- **If Notion tools found:** Great. Check config.md — if `- [ ] Notion connected` is unchecked, update it to `- [x] Notion connected`.
- **If no Notion tools:** That's fine. Say:
  > "Notion isn't connected, so I'll save your draft as a local file instead. If you want me to save directly to Notion next time, I can walk you through connecting it after we finish."

  Continue in local-file mode.

### 4. All clear

If config.md exists, voice is trained, proceed to writing. Don't announce the preflight — just do the work.

---

## What the Agent Does

1. **Find material.** If Notion is connected, scan for recent notes, highlights, and saved ideas from the past 7 days. If not, ask: "What do you want to write about this week? Drop a topic, paste some notes, or point me to a file."
2. **Pick the thread.** Group related ideas. Pick the strongest one. If multiple strong threads, ask which one.
3. **Write the draft** in the user's voice (from config.md voice profile). Format: subject line, intro hook, main body, CTA.
4. **Show the draft.** Do not save yet. Wait for approval or edits.
5. **Save.** On approval: save to Notion (if connected) or local markdown file.
6. **Suggest 3 social media hooks** to promote the newsletter.

## Customization

- **Change the source.** Point it at specific Notion databases instead of scanning everything.
- **Change the format.** If the newsletter has sections (intro, links, takeaway), describe that structure in config.md.
- **Change the frequency.** Weekly, biweekly, or daily digest.

## Rules

- Always show the draft before saving. Never publish directly.
- Use the voice profile for tone and style. If the draft sounds generic, you skipped something.
- If no recent notes found and no topic given, ask. Do not make something up.
- Human writing rules: no AI-tell patterns, vary sentence length, use specific details over vague claims.
- After a successful first run, if Notion was connected during this session, update config.md Setup Status.
