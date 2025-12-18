# Explanation Heavy Content Guide

For conceptual, teaching focused content (like Anchor for dummies courses).

<philosophy>
Teach the "why" so deeply that the "how" becomes obvious. Code illustrates concepts - it's not the primary content.
</philosophy>

<pattern>
## The Explanation Pattern

Build understanding through contrast and progressive revelation:

```
1. Show the PAIN (native/hard way)
2. Show the RELIEF (Anchor/easy way)
3. Explain WHY it works
4. Build up the DETAILS
5. Connect to BIGGER PICTURE
```

**Real example from Anchor for dummies:**
```markdown
In native Solana, every account you receive must be manually validated:

```rust
// Native: 15+ lines of validation
let vault_account = next_account_info(accounts_iter)?;
if vault_account.owner != program_id { ... }
if data[0..8] != VAULT_DISCRIMINATOR { ... }
// ... more checks
```

Miss any of these checks and your program is vulnerable. Now here's the Anchor equivalent:

```rust
#[account(mut)]
pub vault: Account<'info, Vault>,
```

Anchor handles ownership, discriminator, mutability, and deserialization automatically. But to use these abstractions effectively—and debug when things go wrong—you need to understand what's happening under the hood.
```
</pattern>

<structure>
## Document Structure

```markdown
# [Title]

[Hook: Challenge assumption or show stakes - 2-3 paragraphs]

<ArticleSection name="[Why This Matters]" id="[id]" level="h2" />

[Motivation and context - compare approaches]

<ArticleSection name="[General Overview]" id="[id]" level="h2" />

[Foundation concepts with concrete examples]

<ArticleSection name="[Specific Topic 1]" id="[id]" level="h2" />

### [Subtopic]
[Explanation → Code → Deeper explanation]

### [Subtopic]
[Build on previous...]

<ArticleSection name="[Specific Topic N]" id="[id]" level="h2" />

[Same pattern, progressively advanced]
```

**Key rules:**
- Hook before teaching
- Compare before explaining
- Build incrementally (each section builds on previous)
- Cross-reference related lessons where helpful
</structure>

<opening_patterns>
## Strong Opening Patterns

**Show the pain first:**
```markdown
Writing Solana programs without Anchor means manually serializing account data, hand-crafting discriminators, and implementing every security check yourself. A single missed ownership check can drain your program's funds.
```

**Challenge what they think they know:**
```markdown
We saw the `#[account]` macro, but naturally on Solana there are different types of accounts. For this reason it is worth taking a moment to see how generally accounts on Solana work, but more in depth, how they work with Anchor.
```

**Promise insight:**
```markdown
By the end of this course, you'll understand not just how Anchor works, but why its abstractions exist—so you'll know when to rely on them and when to peek under the hood.
```
</opening_patterns>

<comparison_pattern>
## Comparison Pattern

Always show contrast. Understanding comes from difference.

**Native vs Anchor:**
```markdown
In native Solana, every account you receive must be manually validated. Here's what checking a single vault account looks like without Anchor:

```rust
// Native Solana: validating one account
let vault_account = next_account_info(accounts_iter)?;
// Check it's owned by our program
if vault_account.owner != program_id {
    return Err(ProgramError::IncorrectProgramId);
}
// ... 10 more lines
```

Miss any of these checks and your program is vulnerable. Now here's the Anchor equivalent:

```rust
#[account(mut)]
pub vault: Account<'info, Vault>,
```
```

**Before/After within same approach:**
```markdown
Traditional instruction definitions require you to specify exactly which accounts will be used:

```rust
#[derive(Accounts)]
pub struct Transfer<'info> {
    pub from: Account<'info, TokenAccount>,
    pub to: Account<'info, TokenAccount>,
    pub authority: Signer<'info>,
}
```

This works great for single operations, but what if you want to perform multiple token transfers in one instruction?

Remaining accounts let you pass additional accounts that aren't part of the fixed instruction structure:

```rust
// Now we can handle N transfers dynamically
let remaining_accounts = &ctx.remaining_accounts;
```
```
</comparison_pattern>

<code_in_context>
## Code in Explanation Content

Code illustrates concepts. Always wrap with context.

**Before code:**
- What problem does this solve?
- What should readers notice?

**After code:**
- What did we just see?
- What's the key insight?
- Any gotchas?

**Example:**
```markdown
Here's how we're going to initiate the account in our `Account` struct:

```rust
#[account(
    init,
    payer = <target_account>,
    space = <num_bytes>
)]
pub account: Account<'info, CustomAccountType>,
```

Here are some of the fields used in the `#[account]` macro:
- `init`: tells Anchor to create the account
- `payer`: which signer funds the rent
- `space`: how many bytes to allocate
```
</code_in_context>

<progressive_detail>
## Progressive Detail Pattern

Start simple, add complexity motivated by limitations.

```markdown
### Account Structure and Discriminators

Every program account in Anchor needs a way to identify its type. This is handled through discriminators, which can be either:

1. **Default Discriminators**: An 8-byte prefix generated using `sha256("account:<StructName>")[0..8]`

2. **Custom Discriminators**: Starting with Anchor `v0.31.0`, you can specify your own discriminator:

```rust
#[account(discriminator = 1)]              // single-byte
pub struct Escrow { … }
```

**Important Notes about Discriminators**:
- They must be unique across your program
- Using `[1]` prevents using `[1, 2, …]` as these also start with `1`
- `[0]` cannot be used as it conflicts with uninitialized accounts
```

Notice: Start with default → Introduce custom → Add constraints/gotchas
</progressive_detail>

<specific_numbers>
## Specific Numbers & Details

Always include actual values:
- "Maximum size is 10,240 bytes (10 KiB)"
- "8-byte prefix generated using `sha256(...)[0..8]`"
- "Each CPI costs 1000 CU"
- "LazyAccount uses only 24 bytes of stack memory"

Not:
- "Maximum size is limited"
- "A prefix is generated"
- "CPIs have a cost"
</specific_numbers>

<cross_references>
## Cross-References

Link to related content when it helps:
```markdown
If you want to learn more about how to use `anchor-spl` you can follow the [SPL-Token Program with Anchor](/en/courses/spl-token-with-anchor) or [Token2022 Program with Anchor](/en/courses/token-2022-with-anchor) courses.
```

Use when:
- Topic is covered in depth elsewhere
- Reader might need background
- Natural extension of current topic

Avoid:
- Linking to every related concept
- Breaking flow with too many links
</cross_references>

<checklist>
## Explanation Content Review Checklist

- [ ] Opens with hook (stakes, challenge, or promise)
- [ ] Shows comparison early (pain vs relief, before vs after)
- [ ] Explains WHY before HOW
- [ ] Code has context (what to notice, what it means)
- [ ] Builds progressively (simple to complex)
- [ ] Includes specific numbers and measurements
- [ ] Uses `<ArticleSection>` components
- [ ] Cross references related lessons where helpful
- [ ] Closes with insight or next steps
</checklist>

<anti_patterns>
## Explanation Content Anti Patterns

❌ **Starting with definition:**
```markdown
## Account Types

The `Account` type in Anchor is a wrapper around `AccountInfo` that provides automatic validation and deserialization.
```

✅ **Starting with motivation:**
```markdown
## Account Types

In native Solana, every account you receive must be manually validated. Miss any check and your program is vulnerable. Anchor's account types eliminate this entire class of bugs.
```

---

❌ **Code without context:**
```rust
#[derive(Accounts)]
pub struct InstructionAccounts<'info> {
    #[account(mut)]
    pub signer: Signer<'info>,
}
```

✅ **Code with context:**
```markdown
The `Signer` type is used when you need to verify that an account has signed a transaction. This is crucial for security:

```rust
#[derive(Accounts)]
pub struct InstructionAccounts<'info> {
    #[account(mut)]
    pub signer: Signer<'info>,
}
```

The `Signer` type automatically checks if the account has signed the transaction. If it hasn't, the transaction will fail.
```

---

❌ **Vague complexity:**
"This can get complicated in some cases."

✅ **Specific complexity:**
"For larger accounts (over 10,240 bytes), you'll need `zero_copy` and chunked writes."

---

❌ **Flat structure (all concepts at same level):**
```markdown
### Type A
### Type B
### Type C
### Type D
```

✅ **Progressive structure:**
```markdown
### Basic Types (Signer, Account)
### Advanced Types (UncheckedAccount, Box)
### Interface Types (for Token/Token2022 compatibility)
```
</anti_patterns>
