<required_reading>
Read these before proceeding:
1. `references/voice.md` - How to write like Blueshift, what to avoid
2. `references/review-checklist.md` - Full checklist
3. `references/anti-patterns.md` - Common mistakes
</required_reading>

<objective>
Review an entire course by running quick checks on all lessons, then doing full reviews only on lessons that need attention. This is more efficient than reviewing every lesson in depth.
</objective>

<process>
**Step 1: List all lessons**

Get all lesson files in the course directory:
```
ls <course-path>/
```

Read each lesson's `en.mdx` file.

**Step 2: Run quick check on ALL lessons**

For each lesson, check these three things only:

**Opening (first 2-3 paragraphs):**
- Does it create stakes or challenge assumptions?
- ❌ "This lesson covers X" / "We saw X in the previous section"
- ✅ "Without X, attackers can drain your funds"

**Section flow (first 1-2 sentences of each section):**
- Does it explain "why" before "what"?
- ❌ "X is a technique that..."
- ✅ "Solana's 4KB stack limit makes traditional deserialization impossible"

**Closing (last paragraph):**
- Does it zoom out to bigger picture?
- ❌ Ends with code example
- ✅ "This is why X became the de facto standard"

**Step 3: Present summary table**

Output results as a table:

```markdown
## Quick Check Results - [Course Name]

| Lesson | Opening | Section Flow | Closing | Verdict |
|--------|---------|--------------|---------|---------|
| lesson-1 | ✅/⚠️/❌ [brief note] | ✅/⚠️/❌ [brief note] | ✅/⚠️/❌ [brief note] | ✅ OK / ⚠️ Fix X / ❌ Needs review |

## Summary

| Priority | Lessons | Issues |
|----------|---------|--------|
| 🔴 **Needs Full Review** | [list] | [common issues] |
| 🟡 **Fix Specific Issue** | [list] | [what to fix] |
| 🟢 **OK** | [list] | - |
```

**Step 4: Get user decision**

Ask: "Which lessons should I do a full review on?"

Options:
- All red (needs full review)
- All red + yellow
- Specific lessons
- None (just the summary)

**Step 5: Run full reviews**

For each selected lesson:
1. Read `workflows/full-review.md`
2. Determine content type (explanation-heavy vs code-first)
3. Read appropriate content-type reference
4. Apply full checklist
5. Output detailed review with specific fixes

**Step 6: Compile course-level report**

After all reviews, output:

```markdown
## Course Review Summary: [Course Name]

### Overall Assessment
[1-2 sentences on course quality]

### Lessons Reviewed
| Lesson | Status | Key Issues |
|--------|--------|------------|
| ... | ... | ... |

### Common Patterns to Fix
1. [Pattern seen across multiple lessons]
2. [Pattern seen across multiple lessons]

### Recommended Priority
1. [Highest priority fix]
2. [Next priority]
3. [Next priority]
```
</process>

<success_criteria>
- All lessons quick-checked
- Summary table presented
- User chose which to review in depth
- Full reviews completed for selected lessons
- Course-level patterns identified
- Prioritized fix list provided
</success_criteria>
