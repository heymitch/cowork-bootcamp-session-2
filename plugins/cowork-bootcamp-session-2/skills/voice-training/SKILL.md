---
name: voice-training
description: Train your agent on your unique writing voice using the Voice Lab methodology. Say "Train on my voice" or "Learn my writing style". Produces a cached Voice Template that all writing skills use automatically.
---

# Voice Training

Your agent learns how you write. You feed it samples, it extracts your Voice DNA, identifies your archetype mix, maps your vocabulary, fingerprints your sentences, and builds a Voice Template that gets cached and auto-loaded by every writing skill.

## How to Run

- "Train on my voice"
- "Learn my writing style"
- "Here are some writing samples — learn my voice"

---

## Preflight Check (Run Every Time)

Run through this silently. Only speak up if something is missing.

### 1. Does config.md exist?
Read `config.md` from the project root.
- **If missing:** Stop. Say: "I need your business context before training your voice — it helps me understand who you're writing for. Say **'Run my business blueprint'** — takes 5 minutes."
- **If exists:** Continue.

### 2. Already trained?
Check config.md for `- [x] Voice Training completed`.
- **If checked:** Say: "I already have a voice profile saved. Want to retrain with new samples, or keep what we have?"
- **If unchecked:** Continue to training.

### 3. All clear — proceed silently.

---

## The Training Process

Read `references/voice-dna-extraction.md` for the full analysis methodology.

### Step 1: Gather Samples
Ask for 3-5 writing samples they're proud of. Accept pasted text, local files, or Notion pages (if connected). Their best samples are emails, posts, or messages where they were being themselves — not formal reports.

### Step 2: Extract Voice DNA
For each sample, analyze:
- **Voice attributes** — personality traits consistent across all writing (direct, conversational, empathetic, etc.)
- **Style attributes** — technical patterns: word choice, sentence structure, rhythm, figurative language, imagery, point of view

Merge across all samples. Remove duplicates. Keep only unique traits.

### Step 3: Identify Archetype Mix
Read `references/voice-dna-extraction.md` § Archetypes. Analyze the samples against the 5 Voice Archetypes (Storyteller, Opinionator, Fact Presenter, Frameworker, F-Bomber). Output a percentage mix showing which archetypes dominate.

### Step 4: Map Vocabulary
Read `references/voice-refinement.md` § Vocabulary. Audit the samples for:
- **Power Words** — words they use often and love
- **Avoid Words** — words they never use or that feel wrong
- **Replacement Words** — better alternatives (e.g., "use" instead of "utilize")

### Step 5: Fingerprint Sentences
Read `references/voice-refinement.md` § Sentences. Analyze:
- Sentence length range and preferred mix
- Signature sentence starters (do they lead with "But" or "And"?)
- Paragraph length and structure
- Rhetorical question frequency

### Step 6: Catalog Quirks
Read `references/voice-refinement.md` § Quirks. Identify:
- Humor style (dry, witty, self-deprecating, none)
- Metaphor preferences (sports, cooking, tech, everyday)
- Backstory patterns (personal anecdotes, industry war stories)
- Anecdote frequency

### Step 7: Place on Tone Grid
Read `references/voice-refinement.md` § Tone Grid. Rate on two axes:
- **Feel** (1-10): Loose to Tight
- **Attitude** (1-10): Irreverent to Professional

### Step 8: Generate Voice Template
Read `references/voice-template.md` for the exact output format. Compile all findings into the Voice Template format. Show it to the user.

### Step 9: Test with Mimic & Modify
Take a generic paragraph and rewrite it using the Voice Template. Show both versions side by side. Ask: "Does this sound like you?" If not, ask what feels off and adjust.

### Step 10: Cache to config.md
Save the complete Voice Template to `config.md` under `## Voice Profile`. Update `- [x] Voice Training completed` in Setup Status.

This profile is now automatically loaded by all content generation skills via the `<VOICE>` stacking pattern (see `references/voice-stacking.md`).

## Rules

- Never fabricate a voice profile without real samples
- Always show the profile and test output before saving
- If the user says "it doesn't sound like me," ask what specifically feels wrong — don't guess
- Minimum 3 samples. More is better. 10 is ideal.
- You can retrain anytime — just run this skill again with new samples
