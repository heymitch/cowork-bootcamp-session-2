---
name: voice-memo-to-post
description: Turn voice memos, rough notes, and dictated ideas into polished social media posts in your voice. Say "Turn this voice memo into a post" or "Polish these rough notes".
---

# Voice Memo to Post

## What This Does

Turns your messy voice memos and rough notes into polished posts. Record an idea on a walk, during a commute, or in the shower — then run this skill and get a publish-ready post in your voice.

## How to Run

- "Turn this voice memo into a LinkedIn post" + drop the audio file
- "Polish these rough notes into a post: [paste rough notes]"
- "I rambled about [topic] — make it a thread"

---

## Preflight Check (Run Every Time)

Run through this silently. Only speak up if something is missing.

### 1. Does config.md exist?
Read `config.md` from the project root.
- **If missing:** Stop. Say: "I need to know about you and your business first. Say **'Run my business blueprint'** — it takes 5 minutes."
- **If exists:** Continue.

### 2. Is Voice Training complete?
Check config.md for `- [x] Voice Training completed` in the Setup Status section.
- **If unchecked or missing:** Stop. Say: "I can polish this, but it won't sound like you yet. Say **'Train on my voice'** first — I only need to do it once. Then come back with your memo."
- **If checked:** Load the Voice Profile section from config.md. Wrap all content generation with `<VOICE>{profile}</VOICE>`.

### 3. Is Notion connected?
Check your available tools for Notion tools.
- **If found:** Save finished posts to Notion. If config.md has `- [ ] Notion connected`, update to checked.
- **If not found:** Save as local files. Don't mention Notion.

### 4. All clear — proceed silently.

---

## What the Agent Does

1. If audio file provided, transcribe it. Otherwise read the rough text or notes.
2. Extract the core idea. What's the one thing they're saying?
3. Pick the best format: single post, thread, or long-form.
4. Pick the best platform based on content length and style. X for punchy, LinkedIn for depth.
5. Write a polished draft using their voice profile.
6. Preserve their original phrasing where it's strong. Don't over-polish personality out of it.
7. Show the original transcription/notes alongside the polished version.
8. On approval, save to Notion or local file.

## The Key Principle

Your raw voice is gold. This skill cleans it up without killing what made it yours.

**Preserve:** unique phrases, strong opinions, personal stories, specific examples.

**Remove:** filler words, repetition, tangents that don't serve the point, incomplete thoughts that confuse.

**Add:** structure (hook, body, CTA), formatting for the platform, context a reader needs.

## Input Formats Accepted

- Audio files (.m4a, .mp3, .wav, .ogg)
- Rough text pasted directly
- A file path to a text or markdown file with notes
- A Notion page with rough notes

## Rules

- Always show the original alongside the polished version so the user can compare.
- Never add ideas, stats, or examples that weren't in the original. Only reshape what's there.
- Use voice profile for style but lean heavier on the actual words from the memo.
- If the memo is too short or unclear for a full post, ask for one clarifying detail instead of padding.
- Apply human writing rules. No AI patterns.
