<required_reading>
**Always read first:**
1. `references/voice.md` - How to write like Blueshift, what to avoid
2. `references/teaching-method.md` - Core philosophy and techniques

**Then read content type specific guide:**
- Explanation heavy → `references/explanation-content.md`
- Code first → `references/code-first-content.md`

**Also read:**
- Any related lessons mentioned by user (for consistency)
</required_reading>

<process>
**Step 1: Gather context**

Ask using AskUserQuestion:

**Q1: Content type?**
- **Explanation-heavy** - Teaching concepts, comparisons, "why" before "how" (like Anchor-for-dummies)
- **Code-first** - Minimal prose, immediate code, reference-style (like Codama courses)

**Q2: Lesson goal?**
- "What is the ONE thing readers should understand after this lesson?"
- Free text response

**Q3: Target audience?**
- Complete beginners (no Solana experience)
- Basics covered (accounts, transactions, programs)
- Intermediate (has built simple programs)
- Advanced (optimizing existing knowledge)

**Q4: Hook/challenge?** (more important for explanation-heavy)
- "What do readers probably think they know that's incomplete or wrong?"
- This becomes the opening hook
- Free text response

**Q5: Code examples?**
- Yes, I'll provide specific examples
- No, generate appropriate examples
- Use examples from the existing file as base

**Q6: Related lessons?**
- "Are there related lessons to read for consistency?"
- Free text or "None"

**Step 2: Read content-type guide + related content**

Read the appropriate guide:
- Explanation-heavy → `references/explanation-content.md`
- Code-first → `references/code-first-content.md`

If related lessons provided, read them for:
- Terminology consistency
- What's already been covered (avoid repetition)
- Tone and style matching

**Step 3: Plan the structure**

Present plan to user based on content type:

**For Explanation-heavy** (see `references/explanation-content.md` for full patterns):
```markdown
[Hook - challenge assumption or show stakes]

<ArticleSection name="Why This Matters" id="why-this-matters" level="h2" />

[Compare: show the pain (native/hard way) vs the relief (Anchor/easy way)]

<ArticleSection name="[Core Concept]" id="[id]" level="h2" />

### [Subtopic 1]
[Explain motivation → Code with context → Deeper insight]

### [Subtopic 2]
[Build on previous, progressively more advanced]

<ArticleSection name="[Advanced Topic]" id="[id]" level="h2" />

[Continue building...]

[Close with bigger picture insight or link to next lesson]
```

**For Code-first** (see `references/code-first-content.md` for full patterns):
```markdown
# [Title]

[1-2 sentences: What this covers and why]

<ArticleSection name="[Section 1]" id="[id]" level="h2" />

### [Concept A]
To [verb] X, we use `Y`:
```code```
> [Gotcha or note]

### [Concept B]
[Same pattern: brief intro → code → note]

<ArticleSection name="[Section 2]" id="[id]" level="h2" />

[Continue pattern...]
```

**Step 4: Confirm and write**

Ask: "Ready to proceed with this structure?"

If yes, write following the patterns in the content-type guide.

**Step 5: Self-review**

After writing, run through the content-type specific checklist:
- Explanation-heavy: checklist from `references/explanation-content.md`
- Code-first: checklist from `references/code-first-content.md`

Flag any issues for user review.
</process>

<success_criteria>
- Context gathered through questions
- Related lessons read (if provided)
- Structure plan approved by user
- Content written following appropriate type guidelines
- Self-review completed with quick check
</success_criteria>
