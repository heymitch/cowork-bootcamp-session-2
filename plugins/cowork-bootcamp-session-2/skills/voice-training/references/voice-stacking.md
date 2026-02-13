# Voice Stacking — How Writing Skills Use the Cached Profile

Once voice training is complete, the Voice Template lives in `config.md` under `## Voice Profile`. Every writing skill auto-loads it.

## The Pattern

Any content generation prompt wraps the Voice Template in `<VOICE>` tags:

```
[Content prompt — topic, format, length, platform]

<VOICE>
[The full Voice Template from config.md]
</VOICE>

<TEMPLATE>
[Any structural template for the content type]
</TEMPLATE>
```

The voice template guides HOW the content sounds. The content prompt guides WHAT gets written. The structural template guides the FORMAT.

## How Writing Skills Should Load It

### Preflight Voice Check (add to every writing skill)

```
### Voice Check (Silent)
Read config.md → find ## Voice Profile section.
- If section exists and has content: Load the Voice Template. Wrap all content generation with <VOICE>{template}</VOICE>.
- If section is empty or missing: Content will be generated without voice matching. Mention once: "This would sound more like you if we trained on your voice first. Say 'Train on my voice' when you're ready."
- Do NOT block content generation if voice is missing — just note the gap.
```

## Content Type Applications

The same Voice Template works across all formats. The only thing that changes is the content prompt and structural template.

### Short-Form (Tweets, LinkedIn Posts)
```
Write a [length] [platform] post about [topic].

<VOICE>
{Voice Template}
</VOICE>

<TEMPLATE>
{Platform-specific structure}
</TEMPLATE>
```

### Long-Form (Blog Posts, Articles)
```
Write a [length] article about [topic].

<VOICE>
{Voice Template}
</VOICE>

Output: Format as plain text with # for h1 and ## for h2.
```

### Newsletters
```
Write a [length] newsletter introduction about [topic].

<VOICE>
{Voice Template}
</VOICE>
```

### Presentations & Carousels
The voice template applies to slide copy too — it determines whether slides sound casual or polished, punchy or detailed.

## Key Principles

1. **Voice template always loads silently.** Never announce "I'm loading your voice profile" — just use it.
2. **Voice applies to ALL written output.** Posts, emails, proposals, presentation copy, everything.
3. **Voice can be overridden per-piece.** If the user says "make this more formal" or "write this casually," adjust tone while keeping core voice attributes.
4. **Never skip the Avoid Words.** The avoid list is the fastest way to not sound like AI. Check output against it before showing the user.
5. **Archetype mix guides structure.** If their mix is 50% Frameworker, default to framework-style posts. Don't write pure storytelling unless asked.
