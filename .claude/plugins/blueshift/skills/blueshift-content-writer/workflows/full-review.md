<required_reading>
Read in this order:
1. `references/voice.md` - How to write like Blueshift, what to avoid
2. `references/review-checklist.md` - Full checklist with examples
3. `references/anti-patterns.md` - Common mistakes to flag

Then read the content type specific guide (determined in Step 1):
- For explanation heavy: `references/explanation-content.md`
- For code first: `references/code-first-content.md`
</required_reading>

<process>
**Step 1: Determine content type**

Scan the file to identify which type:

| Type | Characteristics | Examples |
|------|-----------------|----------|
| **Explanation-heavy** | Prose explaining "why", comparisons, progressive build-up, code illustrates concepts | Anchor-for-dummies |
| **Code-first** | Minimal prose, immediate code, "To do X, use Y" pattern, blockquote gotchas | Codama courses |

**How to tell:**
- Count paragraphs before first code block: 3+ = explanation-heavy, 1-2 = code-first
- Look for comparison patterns (native vs Anchor) = explanation-heavy
- Look for "To [verb] X, we use Y" pattern = code-first

**After identifying, read the appropriate reference:**
- Explanation-heavy → `references/explanation-content.md`
- Code-first → `references/code-first-content.md`

**Step 2: Run quick check**

Check opening, section flow, and closing (see `<quick_check>` in SKILL.md).

**Step 3: Apply general checklist**

Go through `references/review-checklist.md` - all 12 categories.

**Step 4: Apply content-type specific checklist**

**For explanation-heavy** (from `references/explanation-content.md`):
- [ ] Opens with hook (stakes, challenge, or promise)
- [ ] Shows comparison early (pain vs relief, before vs after)
- [ ] Explains WHY before HOW
- [ ] Code has context (what to notice, what it means)
- [ ] Builds progressively (simple → complex)
- [ ] Includes specific numbers/measurements
- [ ] Cross-references related lessons where helpful
- [ ] Closes with insight or next steps

**For code-first** (from `references/code-first-content.md`):
- [ ] First code block appears within first 5 lines of section
- [ ] Each section follows: intro → code → note pattern
- [ ] Code blocks under 15 lines (unless complete examples)
- [ ] No placeholder values without instructions
- [ ] All code is copy-paste ready
- [ ] Blockquotes used for gotchas (not inline warnings)
- [ ] External docs linked where applicable
- [ ] Consistent H3 structure throughout

**Step 5: Check for anti-patterns**

Scan against `references/anti-patterns.md` AND the anti-patterns in the content-type reference.
</process>

<output_format>
```markdown
## Review Summary

**Content Type**: [Explanation-heavy / Code-heavy / Reference]
**Overall Assessment**: [1-2 sentences]

## Critical Issues
- **[Issue]**: [Location/line] - [Specific fix]

## Improvements
- **[Suggestion]**: [Location] - [Why it helps]

## Content-Type Specific
- [Relevant findings for this content type]

## Strengths
- [What works well]

## Checklist Score
[X/12 categories passing]
```
</output_format>

<success_criteria>
- Content type correctly identified
- All 12 checklist categories evaluated
- Anti-patterns checked
- Content-type specific checks applied
- Actionable feedback with specific locations and fixes
</success_criteria>
