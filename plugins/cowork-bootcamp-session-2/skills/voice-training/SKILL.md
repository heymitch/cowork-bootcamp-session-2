---
name: voice-training
description: Train your agent on your unique writing voice so all outputs sound like you, not generic AI. Say "Train on my voice" or "Learn my writing style".
---

# Voice Training

## What This Does

Learns how you write. You feed it examples of your best writing, and it creates a voice profile your agent uses for everything it writes. The difference: AI writing that makes you cringe vs. AI writing that makes you think "wait, did I write this?"

## How to Run

- "Train on my voice"
- "Learn my writing style"
- "Here are some writing samples — learn my voice"

---

## Preflight Check (Run Every Time)

Run through this silently. Only speak up if something is missing.

### 1. Does config.md exist?
Read `config.md` from the project root.
- **If missing:** Stop. Say: "I need your business context before training your voice — it helps me understand the context your writing lives in. Say **'Run my business blueprint'** — it takes 5 minutes. Then come back and say 'Train on my voice'."
- **If exists:** Continue.

### 2. Is Notion connected? (Optional)
Check for Notion tools.
- **If found:** Can pull writing samples from Notion pages. Update config.md if unchecked.
- **If not found:** User will paste samples or point to local files.

### 3. Already trained?
Check config.md for `- [x] Voice Training completed`.
- **If checked:** Say: "I already have a voice profile saved. Want to retrain with new samples, or keep what we have?"
- **If unchecked:** Continue to training.

### 4. All clear — proceed silently.

---

## The Training Process

### Step 1: Gather Samples

Ask the user for 3-5 writing samples they're proud of. Accept any of these:

- Paste text directly into the chat
- Point to files on their computer
- Point to Notion pages (if Notion is connected)
- Point to a folder of past writing

### Step 2: Analyze Patterns

Read every sample and look for:

- **Sentence length** — Short and punchy? Long and flowing? A mix?
- **Word choice** — Casual? Technical? Slang? Simple?
- **Structure habits** — How do they open? Close? Transition between ideas?
- **Personality markers** — Humor? Directness? Storytelling? Data-driven?
- **Formatting preferences** — Bullets? Headers? Long paragraphs? One-liners?

### Step 3: Show the Voice Profile

Write up a summary: "Here's what I learned about your writing style: ..."

Include specific examples pulled from their samples. Don't be vague. Quote them.

### Step 4: Run a Test

Take a generic paragraph and rewrite it in their voice. Show both versions side by side:

- **Generic version** — the bland AI default
- **Voice-matched version** — rewritten to sound like them

Ask: "Does this sound like you?"

### Step 5: Save (If Approved)

Save the voice profile to `config.md`. If one already exists, update it.

**Then update the Setup Status section in config.md:** change `- [ ] Voice Training completed` to `- [x] Voice Training completed`.

This is critical — other skills check this checkbox to know if voice is ready.

### Step 6: Refine (If Needed)

If they say it's not right, don't guess. Ask: "What feels off?" Then adjust and test again.

## What Gets Saved

A voice profile section in `config.md` containing:

- **Writing style summary** — 2-3 sentences capturing their voice
- **Key patterns** — Bullet list of their habits
- **Words/phrases they use often**
- **Words/phrases they'd never use**
- **2-3 short sample excerpts** as reference anchors

This profile is automatically loaded by all other content skills.

## Tips

- Your best samples are emails, posts, or messages where you were being yourself — not formal reports.
- The more samples, the better. 3 is minimum, 10 is ideal.
- You can retrain anytime — just run this skill again with new samples.

## Rules

- Never fabricate a voice profile without real samples.
- Always show the profile and test output before saving.
- Start with the human writing rules (no AI-tell patterns) as a baseline. The voice profile builds ON TOP OF that baseline.
- If the user says "it doesn't sound like me," ask specifically what's wrong rather than guessing.
