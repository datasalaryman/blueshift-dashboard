# Anti-Patterns

Common mistakes to flag during review.

<mistakes>
## ❌ Mistakes to Flag

**Assuming Knowledge**
- "As we saw in the previous section..."
- "You already know that..."
- Starting with "We" without establishing context

**Solution Before Problem**
- "Zero-copy deserialization bypasses... This is useful for large accounts."
- Showing the fix before showing what breaks

**Vague Warnings**
- "Be careful with this!"
- "This is important!"
- "Make sure to handle errors"

**Over-Simplification**
- "Just add this line and it works!"
- "Simply call the function"
- Using "simply" or "just" anywhere

**No Stakes Opening**
- "This lesson covers X"
- "In this section we'll learn about Y"
- Starting with definition instead of why it matters

**Missing Trade-offs**
- "Use X" without explaining when NOT to use X
- "X is better" without explaining what you give up
- Presenting one approach as universally correct

**Abstract Before Concrete**
- Definition before relatable example
- Theory before practical scenario
- "X is a Y that does Z" as the opening

**Incomplete Code**
- `// ... rest of code`
- Missing imports
- Placeholder values without instructions
- Code that won't run if copy-pasted

**Passive Voice**
- "The account is created by..."
- "It can be seen that..."
- "The function is called"

**Vague Error References**
- "You might see an error"
- "This can cause problems"
- "Be aware of potential issues"
</mistakes>

<fixes>
## ✅ How to Fix Them

**Challenge, Don't Assume**
- "Most developers think accounts are just data containers."
- "You might expect this to work like Ethereum, but..."

**Problem Before Solution**
- "Solana's 4KB stack limit makes traditional deserialization impossible. Zero-copy solves this by..."
- Show the error first, then the fix

**Specific Warnings**
- "The init constraint is limited to 10,240 bytes due to CPI limitations."
- "This will fail silently if the account doesn't exist."

**Honest Complexity**
- "This requires understanding memory layout, but it's the only way to..."
- "The setup takes 5 steps, but each one is straightforward."

**Stakes First**
- "Without this check, anyone can drain your vault."
- "A single missing validation can cost millions."

**Trade-offs Clear**
- "Anchor adds compile time but eliminates entire vulnerability classes."
- "Zero-copy is faster but requires unsafe Rust knowledge."

**Concrete First**
- "Imagine you're building a game with 50KB player stats..."
- "Picture a vault that holds user funds..."

**Complete Code**
- Show all imports at top
- Provide working examples
- Note any setup requirements

**Active Voice**
- "You create the account by..."
- "The function returns..."
- "This check prevents..."

**Specific Errors**
- `Error: Stack offset of -30728 exceeded max offset of -4096`
- Include actual error messages developers will see
</fixes>
