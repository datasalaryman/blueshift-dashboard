# Review Checklist

Use this when reviewing or writing content. Each item includes what to look for and examples.

<checklist>

## 1. Opening Strength (First 2-3 Paragraphs)

- [ ] **Creates stakes or challenges assumptions**
  - Test: Does it make reader think "I need to understand this"?
  - ✅ Good: "Without owner checks, attackers can drain your program's funds"
  - ❌ Weak: "Owner checks are important for security"

- [ ] **Defines what the topic IS in plain language**
  - Test: Can a beginner understand what we're talking about?
  - ✅ Good: "Owner checks verify an account is owned by the expected program"
  - ❌ Weak: "This lesson covers validation patterns"

- [ ] **Avoids assuming knowledge**
  - Test: Does it start with "We saw..." or "As you know..."?
  - ✅ Good: Establishes context from scratch or challenges what they think
  - ❌ Weak: "In the previous section, we covered X, now let's look at Y"

## 2. Section Structure & Flow

- [ ] **Each major section starts with "why" in first 1-2 sentences**
  - Test: Can you find the motivation before the explanation?
  - ✅ Good: "Solana's 4KB stack limit makes traditional deserialization impossible for large accounts"
  - ❌ Weak: "Zero-copy is a technique that... This is useful when accounts are large."

- [ ] **One idea per section**
  - Test: Can you summarize the section in one sentence?

- [ ] **Paragraphs are 2-4 sentences maximum**

## 3. Concrete Before Abstract

- [ ] **Advanced techniques include concrete scenarios**
  - Pattern: Scenario → Problem → Why Simple Fails → Solution
  - ✅ "You're building a game with 50KB player stats → Stack is only 4KB → Zero-copy accesses memory directly"
  - ❌ "Zero-copy is a technique for working with large accounts..."

- [ ] **Abstract concepts grounded in relatable examples first**
  - ✅ "PDAs are like safety deposit boxes: the bank can open them using its master key"
  - ❌ "PDAs are deterministically derived addresses without private keys"

## 4. Show Failure First

- [ ] **Security vulnerabilities show attack vector**
  - Pattern: Vulnerable code → "At first glance this looks secure" → Concrete attack steps → Fix

- [ ] **Optimizations show the performance problem first**
  - Include actual errors or measurements
  - ✅ "Stack offset of -30728 exceeded max offset of -4096"
  - ❌ "This approach can cause problems"

- [ ] **Alternative approaches show trade-offs**
  - ✅ "Anchor adds compile time but eliminates security bugs"
  - ❌ "Anchor is better"

## 5. Code Presentation

- [ ] **Context before code**
  - What are we building? What problem does this solve?

- [ ] **Code blocks have explanatory text AFTER**
  - Highlight what the code accomplishes
  - Point out important patterns or gotchas

- [ ] **Examples are minimal and focused**
  - Teaching one specific thing
  - Every line serves the lesson
  - Under 20 lines per code block (higher completion rates)

- [ ] **Code is copy paste runnable**
  - No placeholder values like `<YOUR_KEY>` without instructions
  - Imports/dependencies shown or noted
  - ❌ `// ... rest of code` - show complete examples

## 6. Technical Accuracy & Depth

- [ ] **Specific measurements included**
  - "10,240 bytes", "32KB heap", "4KB stack", "5,000 lamports"

- [ ] **Implementation details explained**
  - ✅ "Uses sha256('account:VaultAccount')[0..8] as discriminator"
  - ❌ "Anchor generates a discriminator"

- [ ] **Trade offs explicitly stated**
  - Never just "do this" - explain costs/benefits

## 7. Discovery Pattern

- [ ] **Readers reach conclusions, not told them**
  - ✅ "PDAs can sign CPIs on the program's behalf. They provide deterministic addresses."
  - ❌ "PDAs are powerful because they can sign CPIs"

## 8. Comparisons

- [ ] **Uses comparison to build understanding**
  - Framework: "Unlike Anchor, Pinocchio..."
  - Before and after: "Without this check... With this check..."

## 9. Formatting & Structure

- [ ] **Key terms bolded on first use ONLY**
- [ ] **Inline code for functions, types, commands**
- [ ] **Blockquotes only for gotchas, tips, insights**
- [ ] **Headers follow hierarchy** (H1: title, H2: sections, H3: subsections)

## 10. Closing

- [ ] **Ends with bigger picture insight**
  - ✅ "This is why Anchor has become the de facto standard: it eliminates vulnerability classes"
  - ❌ Ends with final code example and no reflection

## 11. Content Quality

- [ ] **No unexplained jargon**
- [ ] **Difficulty acknowledged honestly** (never "simply" or "just")
- [ ] **Credits given where applicable**

## 12. Accessibility & Clarity

- [ ] **Active voice, second person ("you")**
  - ✅ "You create an account" → ❌ "An account is created"

- [ ] **Write for all readers**
  - Avoid idioms, cultural references that don't translate
  - Define acronyms on first use

- [ ] **Scannable structure**
  - Short paragraphs (2-4 sentences max)
  - Meaningful headings that work as standalone labels
  - Key information front-loaded in each section

- [ ] **Show actual error messages**
  - Use real errors developers will encounter
  - ✅ `Error: Stack offset of -30728 exceeded max offset of -4096`
  - ❌ "You might see a stack error"

</checklist>
