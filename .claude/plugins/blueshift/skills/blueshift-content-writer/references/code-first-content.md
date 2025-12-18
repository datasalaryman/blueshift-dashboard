# Code First Content Guide

For documentation style, reference, and tutorial content (like Codama courses).

<philosophy>
Code is why developers come. Get to it immediately. Prose supports the code, not the other way around.
</philosophy>

<pattern>
## The Code First Pattern

Every section follows this structure:

```
### [Node/Concept Name]

[1-2 sentences: What it is and when to use it]

[Code block - the primary content]

> [Blockquote: Gotcha, note, or important caveat]
```

**Real example from Codama:**
```markdown
### Value Node

To pass specific values into a node, we use `ValueNode`. This type represents all available value nodes that can hold different types of data.

[Here](link) you can find detailed documentation on all the values available.

> `ValueNode` is a type alias and cannot be used directly as a node. When a `ValueNode` is required, use one of the specific value node types instead.
```
</pattern>

<structure>
## Document Structure

```markdown
# [Title]

[1-2 sentence intro: What this covers and why]

<ArticleSection name="[Section Name]" id="[id]" level="h2" />

### [Subsection 1]
[Brief intro]
[Code]
[Note if needed]

### [Subsection 2]
[Same pattern...]

### [Subsection N]
[Same pattern...]
```

**Key rules:**
- Use `<ArticleSection>` component for major sections
- H3 (`###`) for individual concepts within a section
- No H2 (`##`) directly in markdown - use the component
</structure>

<code_rules>
## Code Block Rules

**Length:**
- Keep under 15 lines for single-concept examples
- Longer examples OK for complete working code
- Break complex examples into steps

**Context:**
- 1-2 sentences before explaining what this code does
- Inline comments only for non-obvious parts
- No `// ... rest of code` - show complete examples

**Format:**
```ts
// Good: Focused, complete, copy-paste ready
const pdaSeedNode = constantPdaSeedNode(stringTypeNode('utf8'), stringValueNode('auth'));
```

```ts
// Bad: Too much, unfocused
const pdaSeedNode = constantPdaSeedNode(
    stringTypeNode('utf8'),  // The type of the seed
    stringValueNode('auth')  // The value - this is the string "auth"
);
// You can also use other types here
// For example, you could use a number type
// etc...
```

**Multiple variants:**
When showing multiple ways to do something, use bullet list + code:

```markdown
- `ConstantPdaSeedNode`: Used to describe a constant seed. Takes a `TypeNode` and `ValueNode`:

    ```ts
    const pdaSeedNode = constantPdaSeedNode(stringTypeNode('utf8'), stringValueNode('auth'));
    ```

- `VariablePdaSeedNode`: Used for variable seeds. Takes a name and `TypeNode`:

    ```ts
    const pdaSeedNode = variablePdaSeedNode('authority', publicKeyTypeNode())
    ```
```
</code_rules>

<prose_rules>
## Prose Rules

**Opening sentences - use these patterns:**
- "To [verb] X, we use `Y`."
- "For [goal], use `X`."
- "[Node/Type] allows you to [capability]."

**Avoid:**
- Long explanations before showing code
- "In this section we will learn..."
- Multiple paragraphs before the first code block

**Notes and gotchas:**
Use blockquotes (`>`) for:
- Type alias warnings
- Important caveats
- Links to external docs

```markdown
> `ValueNode` is a type alias and cannot be used directly as a node.
```

**External links:**
Link to source docs for comprehensive info:
```markdown
[Here](https://github.com/codama-idl/codama/blob/main/packages/nodes/docs/valueNodes/README.md) you can find detailed documentation.
```
</prose_rules>

<checklist>
## Code First Review Checklist

- [ ] First code block appears within first 5 lines of section
- [ ] Each section follows: intro → code → note pattern
- [ ] Code blocks under 15 lines (unless complete examples)
- [ ] No placeholder values without instructions
- [ ] All code is copy paste ready
- [ ] Blockquotes used for gotchas (not inline warnings)
- [ ] External docs linked where applicable
- [ ] Consistent H3 structure throughout
- [ ] `<ArticleSection>` used for major sections
</checklist>

<anti_patterns>
## Code First Anti Patterns

❌ **Too much prose before code:**
```markdown
### Value Node

Value nodes are an important concept in Codama. They allow you to pass specific values into other nodes. There are many different types of value nodes available, each serving a different purpose. Understanding value nodes is essential for building your IDL correctly. Let's look at how to use them.

```ts
const node = valueNode(...)
```
```

✅ **Code first:**
```markdown
### Value Node

To pass specific values into a node, we use `ValueNode`:

```ts
const node = valueNode(...)
```
```

---

❌ **Explaining what code does line by line:**
```ts
const node = programNode({
    name: 'counter',      // The name of the program
    publicKey: '222...',  // The program's public key
    version: '0.0.1',     // The version number
    // ... 10 more comments
});
```

✅ **Let code speak, note the non obvious:**
```ts
const node = programNode({
    name: 'counter',
    publicKey: '22222222222222222222222222222222222222222222',
    version: '0.0.1',
    docs: [],
    accounts: [],
    instructions: [],
});
```
> The `publicKey` uses placeholder `222...` in examples. In production, use your actual program ID.

---

❌ **Vague references to "more information":**
"There are many more options available which we won't cover here."

✅ **Link to the actual docs:**
"[Here](link) you can find detailed documentation on all available options."
</anti_patterns>
