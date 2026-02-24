# Cursor Rules

Rules give the AI persistent context about your project. They live in `.cursor/rules/` and apply automatically when relevant files are open.

## What Are Rules?

- **Project-specific** — Stored in the repo, shared with everyone who clones it
- **Context for the AI** — Coding standards, naming conventions, patterns
- **File-aware** — Can apply to all files or only when you work with specific types (e.g. `**/*.ts`, `backend/**/*.py`)

## Rule File Format

Rules are `.mdc` files with YAML frontmatter:

```markdown
---
description: Brief description of what this rule does
globs: **/*.ts
alwaysApply: false
---

# Rule Title

Your rule content here...
```

### Frontmatter Fields

| Field | Type | Description |
|-------|------|-------------|
| `description` | string | What the rule does (shown in rule picker) |
| `globs` | string | File pattern — rule applies when matching files are open |
| `alwaysApply` | boolean | If `true`, applies to every conversation |

## When to Use What

| Use Case | `alwaysApply` | `globs` |
|----------|---------------|---------|
| Universal standards (e.g. error handling) | `true` | — |
| TypeScript conventions | `false` | `**/*.ts` |
| React patterns | `false` | `**/*.tsx` |
| API conventions | `false` | `**/api/**/*.py` |

## Best Practices

1. **Keep rules concise** — Under 50 lines per rule
2. **One concern per rule** — Split large rules into focused pieces
3. **Be actionable** — Write like clear internal docs
4. **Include examples** — Show good vs bad patterns

## Example: TypeScript Standards

```markdown
---
description: TypeScript coding standards
globs: **/*.ts
alwaysApply: false
---

# Error Handling

- Always log errors before rethrowing
- Use typed error classes when possible

\`\`\`typescript
// ❌ BAD
try { await fetchData(); } catch (e) {}

// ✅ GOOD
try {
  await fetchData();
} catch (e) {
  logger.error('Failed to fetch', { error: e });
  throw new DataFetchError('Unable to retrieve data', { cause: e });
}
\`\`\`
```

## Where Rules Live

```
your-project/
└── .cursor/
    └── rules/
        ├── typescript-standards.mdc
        ├── react-patterns.mdc
        └── api-conventions.mdc
```

## Rules vs Skills

| | Rules | Skills |
|---|-------|--------|
| **Scope** | Project (in repo) | Personal or project |
| **Purpose** | Conventions, standards | Workflows, multi-step tasks |
| **Trigger** | File patterns / always | User phrases, explicit mention |
| **Example** | "Use functional components" | "Review this PR using our checklist" |

Rules = *what* the AI should follow. Skills = *how* the AI should do specific tasks.
