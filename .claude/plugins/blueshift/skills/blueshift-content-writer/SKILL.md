---
name: blueshift-content-writer
description: Reviews and writes Solana educational content following the Blueshift teaching method. Use when reviewing MDX course lessons, analyzing lesson structure, evaluating technical writing, writing new lessons, or providing content feedback.
allowed-tools: Read, Grep, Glob, WebFetch
---

<objective>
Create and review technical educational content that works for everyone - from complete beginners to senior developers - by following the Blueshift philosophy: **Teach the "why" so deeply that the "how" becomes obvious.**
</objective>

<essential_principles>
**The 10 Teaching Techniques**

1. **Challenge Before You Teach** - Acknowledge what readers "know", then show it's incomplete
2. **Concrete Before Abstract** - Ground concepts in physical/relatable scenarios first
3. **Show the Failure First** - Demonstrate WHY by showing what happens without it
4. **Explain Trade-offs, Not Rules** - Never say "do this" without explaining costs/benefits
5. **Build Incrementally** - Each piece motivated by limitations of the previous
6. **Compare Constantly** - Understanding comes from contrast
7. **Acknowledge the Hard Parts** - Never pretend difficulty is easy
8. **One Idea Per Section** - If you can't summarize in one sentence, split it
9. **Make Readers Discover** - Structure so readers reach conclusions themselves
10. **Close with Bigger Picture** - End by zooming out to broader implications

**Content Types**

| Type | Characteristics | Examples |
|------|-----------------|----------|
| **Explanation-heavy** | Teaching concepts, prose explaining "why", code illustrates ideas | Anchor-for-dummies |
| **Code-first** | Step-by-step how-to, code blocks with minimal prose, reference-style | Codama courses |
</essential_principles>

<intake>
**Step 1: Get the content**

Ask: "What content should I work with?"

Accept either:
- **Single lesson**: `src/app/content/courses/anchor-for-dummies/anchor-101/en.mdx`
- **Entire course**: `src/app/content/courses/anchor-for-dummies/` (directory)
- **GitHub URL**: `https://github.com/user/repo/blob/main/path/to/file.mdx`

**Detecting input type:**
- Ends with `/` or is a directory → Course review (use `workflows/course-review.md`)
- Starts with `http` → URL (use WebFetch)
- Ends with `.mdx` → Single lesson (use Read)

**For GitHub URLs:**
- Convert `github.com/.../blob/...` to `raw.githubusercontent.com/...` automatically
- Use WebFetch with prompt: "Return the complete raw content of this file exactly as-is"

**Wait for response. Fetch/read the content before proceeding.**

**Step 2: Choose action**

**For single lessons**, present options:
1. **Review** - Full review against Blueshift checklist
2. **Write** - Write new content (provide guidance and structure)
3. **Quick check** - Fast 30-second review of key elements

**For entire courses**, automatically use `workflows/course-review.md`:
- Quick check all lessons first
- Present summary table
- Ask which lessons need full review
- Run full reviews on selected lessons

**Wait for response before proceeding.**
</intake>

<routing>
| Input Type | Response | Action |
|------------|----------|--------|
| Directory/course | (auto) | Read `workflows/course-review.md` and follow it |
| Single lesson | 1, "review" | Read `workflows/full-review.md` and follow it |
| Single lesson | 2, "write" | Read `workflows/write-content.md` and follow it |
| Single lesson | 3, "quick" | Use `<quick_check>` below (no file read needed) |

**After determining intent, follow the appropriate workflow.**
</routing>

<quick_check>
**Fast 30-second review** - Check these three things only:

**1. Opening (first 2-3 paragraphs)**
- Does it create stakes or challenge assumptions?
- ❌ "Owner checks are important"
- ✅ "Without owner checks, attackers drain your funds"

**2. Each section start (first 1-2 sentences)**
- Does it explain "why" before "what"?
- ❌ "Zero-copy is a technique..."
- ✅ "Solana's 4KB stack limit makes traditional deserialization impossible"

**3. Closing (last paragraph)**
- Does it zoom out to bigger picture?
- ❌ Ends with code example
- ✅ "This is why Anchor became the de facto standard"

**Output format:**
```
## Quick Check Results

**Opening**: ✅/❌ [1 sentence assessment]
**Section Flow**: ✅/❌ [1 sentence assessment]
**Closing**: ✅/❌ [1 sentence assessment]

**Recommendation**: [Pass / Recommend full review]
```

If any fail, recommend full review.
</quick_check>

<workflows_index>
| Workflow | Purpose |
|----------|---------|
| `workflows/course-review.md` | Review entire course (quick check all → full review selected) |
| `workflows/full-review.md` | Comprehensive review of single lesson |
| `workflows/write-content.md` | Write new content with context gathering |
</workflows_index>

<references_index>
| Reference | Contains |
|-----------|----------|
| `references/voice.md` | **Read first.** How to write like Blueshift, what to avoid |
| `references/teaching-method.md` | 10 techniques, Blueshift formula |
| `references/review-checklist.md` | 12 category checklist with examples |
| `references/anti-patterns.md` | Common mistakes and how to fix them |
| `references/explanation-content.md` | Guide for explanation heavy content (like Anchor for dummies) |
| `references/code-first-content.md` | Guide for code first content (like Codama courses) |
</references_index>

<success_criteria>
Content following this method should:

1. **Work for all skill levels** - Beginners can follow, experts appreciate depth
2. **Build intuition** - Readers understand "why", not just "what"
3. **Create "aha moments"** - Concepts click rather than being memorized
4. **Feel earned** - Solutions make sense because problems were shown
5. **Stay memorable** - Bigger picture connections stick with readers

The goal: readers feel smarter, not just more informed.
</success_criteria>
