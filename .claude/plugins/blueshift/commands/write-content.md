---
description: Write new educational content using the Blueshift teaching methodology.
allowed-tools: Read, Grep, Glob, WebFetch, Task, AskUserQuestion
---

# Write Content

You are writing educational content using the Blueshift methodology. Your goal is to teach the "why" so deeply that the "how" becomes obvious.

## Input: $ARGUMENTS

If no arguments provided, ask: "What content should I write? Give me a topic or an existing file to expand."

## Load Required References

Before writing anything, read these files in order:

1. `${CLAUDE_PLUGIN_ROOT}/skills/blueshift-content-writer/references/voice.md`
2. `${CLAUDE_PLUGIN_ROOT}/skills/blueshift-content-writer/references/teaching-method.md`

## Gather Context

Ask using AskUserQuestion:

**Q1: Content type?**
- Explanation heavy (teaching concepts, comparisons, "why" before "how")
- Code first (minimal prose, immediate code, reference style)

**Q2: Lesson goal?**
"What is the ONE thing readers should understand after this lesson?"

**Q3: Target audience?**
- Complete beginners (no Solana experience)
- Basics covered (accounts, transactions, programs)
- Intermediate (has built simple programs)
- Advanced (optimizing existing knowledge)

**Q4: Hook or challenge?**
"What do readers probably think they know that's incomplete or wrong?"

**Q5: Related lessons?**
"Are there related lessons to read for consistency?" (provide paths or "None")

## Read Content Type Guide

Based on Q1:
- Explanation heavy → Read `${CLAUDE_PLUGIN_ROOT}/skills/blueshift-content-writer/references/explanation-content.md`
- Code first → Read `${CLAUDE_PLUGIN_ROOT}/skills/blueshift-content-writer/references/code-first-content.md`

If related lessons provided, read them for terminology consistency.

## Plan Structure

Present plan to user based on content type:

**For Explanation heavy:**
```
[Hook that challenges assumption or shows stakes]

<ArticleSection name="Why This Matters" id="why-this-matters" level="h2" />
[Compare: show the pain vs the relief]

<ArticleSection name="[Core Concept]" id="[id]" level="h2" />
### [Subtopic 1]
[Explain motivation → Code with context → Deeper insight]

### [Subtopic 2]
[Build on previous, progressively more advanced]

[Close with bigger picture insight]
```

**For Code first:**
```
# [Title]
[1-2 sentences: What this covers and why]

<ArticleSection name="[Section 1]" id="[id]" level="h2" />
### [Concept A]
To [verb] X, we use `Y`:
[code]
> [Gotcha or note]

[Continue pattern...]
```

Ask: "Ready to proceed with this structure?"

## Write

Follow the patterns in the content type guide. Remember:
- No hyphens in concept names
- No AI transitions ("Furthermore", "Additionally")
- Be direct, not formal
- Specific numbers always
- Short sentences hit harder

## Self Review

After writing, check against:
- `${CLAUDE_PLUGIN_ROOT}/skills/blueshift-content-writer/references/voice.md` (tone check)
- The content type checklist

Flag any issues for user review.
