---
description: Review educational content using the Blueshift teaching methodology. Supports single lessons or entire courses.
allowed-tools: Read, Grep, Glob, WebFetch, Task
---

# Review Content

You are reviewing educational content using the Blueshift methodology. Your goal is to ensure content teaches the "why" so deeply that the "how" becomes obvious.

## Input: $ARGUMENTS

If no arguments provided, ask: "What content should I review? Provide a file path, directory, or GitHub URL."

## Determine Input Type

- Ends with `/` or is a directory → Course review (multiple lessons)
- Starts with `http` → GitHub URL (convert to raw URL and fetch)
- Ends with `.mdx` → Single lesson review

For GitHub URLs, convert `github.com/.../blob/...` to `raw.githubusercontent.com/...` and use WebFetch.

## Load Required References

Before reviewing, read these files in order:

1. `${CLAUDE_PLUGIN_ROOT}/skills/blueshift-content-writer/references/voice.md`
2. `${CLAUDE_PLUGIN_ROOT}/skills/blueshift-content-writer/references/review-checklist.md`
3. `${CLAUDE_PLUGIN_ROOT}/skills/blueshift-content-writer/references/anti-patterns.md`

## For Single Lesson Review

**Step 1: Quick Check**

Check opening, section flow, and closing:
- Opening: Does it create stakes or challenge assumptions?
- Section Flow: Does each section explain "why" before "what"?
- Closing: Does it zoom out to bigger picture?

**Step 2: Determine Content Type**

- Explanation heavy: 3+ paragraphs before first code, comparisons, progressive build up
- Code first: Minimal prose, immediate code, "To do X, use Y" pattern

**Step 3: Read Content Type Guide**

- Explanation heavy → `${CLAUDE_PLUGIN_ROOT}/skills/blueshift-content-writer/references/explanation-content.md`
- Code first → `${CLAUDE_PLUGIN_ROOT}/skills/blueshift-content-writer/references/code-first-content.md`

**Step 4: Apply Full Checklist**

Go through all 12 categories from review-checklist.md.

**Step 5: Check Anti patterns**

Scan against anti-patterns.md AND the content type specific anti patterns.

**Step 6: Voice Check**

Does it sound like:
- A knowledgeable friend explaining something? Good
- A textbook or documentation? Flag it
- An AI chatbot? Flag it hard

Check for: hyphens in concept names, AI transitions, empty intensifiers, passive hedging.

**Output Format:**
```
## Review Summary

**Content Type**: [Explanation heavy / Code first]
**Overall Assessment**: [1-2 sentences]

## Critical Issues
- **[Issue]**: [Location/line] - [Specific fix]

## Voice Issues
- [Any AI sounding language, hyphens in concepts, formal transitions]

## Improvements
- **[Suggestion]**: [Location] - [Why it helps]

## Strengths
- [What works well]

## Checklist Score
[X/12 categories passing]
```

## For Course Review (Directory)

1. List all lessons in the directory
2. Run quick check on ALL lessons
3. Present summary table:

```
## Quick Check Results

| Lesson | Opening | Section Flow | Closing | Verdict |
|--------|---------|--------------|---------|---------|
| lesson-1 | ✅/❌ | ✅/❌ | ✅/❌ | OK / Needs review |

## Summary
| Priority | Lessons | Issues |
|----------|---------|--------|
| Needs Full Review | [list] | [common issues] |
| OK | [list] | - |
```

4. Ask which lessons need full review
5. Run full reviews on selected lessons
6. Compile course level report with common patterns
