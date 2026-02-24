# Cursor Skills

Skills teach the AI how to perform specific workflows: code reviews, commit messages, database queries, or any multi-step task.

## What Are Skills?

- **Instructions for the AI** — Step-by-step guidance for specialized tasks
- **Triggered by context** — The AI applies them when your request matches the skill’s description
- **Personal or shared** — Can live in your home directory or in the project

## Where Skills Live

| Type | Path | Scope |
|------|------|-------|
| Personal | `~/.cursor/skills/skill-name/` | All your projects |
| Project | `.cursor/skills/skill-name/` | Shared with anyone using the repo |

**Important:** Don’t create skills in `~/.cursor/skills-cursor/` — that’s for Cursor’s built-in skills.

## Skill Structure

Each skill is a directory with a `SKILL.md` file:

```
skill-name/
├── SKILL.md              # Required — main instructions
├── reference.md          # Optional — detailed docs
├── examples.md           # Optional — usage examples
└── scripts/              # Optional — utility scripts
```

## SKILL.md Format

```markdown
---
name: your-skill-name
description: Brief description of what this skill does and when to use it
---

# Your Skill Name

## Instructions
Clear, step-by-step guidance for the agent.

## Examples
Concrete examples of using this skill.
```

### Required Metadata

| Field | Requirements |
|-------|--------------|
| `name` | Max 64 chars, lowercase, hyphens only |
| `description` | Max 1024 chars — **critical** for discovery |

## Writing Good Descriptions

The description tells the AI *when* to use the skill. Include:

1. **WHAT** — What the skill does
2. **WHEN** — Trigger phrases or scenarios

**Good:**
```yaml
description: Generate descriptive commit messages by analyzing git diffs. Use when the user asks for help writing commit messages or reviewing staged changes.
```

**Vague:**
```yaml
description: Helps with commits
```

Write in **third person** — the description is injected into the system prompt.

## Common Patterns

### Template Pattern
Provide output format templates (e.g. report structure, commit message format).

### Workflow Pattern
Break complex tasks into steps with checklists.

### Examples Pattern
Show input/output examples when quality depends on seeing concrete cases.

## Skills vs Rules

| | Rules | Skills |
|---|-------|--------|
| **Purpose** | Conventions, standards | Workflows, multi-step tasks |
| **Trigger** | File patterns / always | User phrases, context |
| **Example** | "Use functional components" | "Review this PR using our checklist" |

## Using Existing Skills

Cursor ships with built-in skills. You can also:

- **Install skills** — From curated lists or GitHub repos
- **Create project skills** — Add `.cursor/skills/` to your repo for team-wide use
- **Create personal skills** — Add to `~/.cursor/skills/` for your own workflows

## Creating a New Skill

1. **Gather requirements** — Purpose, scope, trigger scenarios
2. **Choose location** — Personal vs project
3. **Draft name and description** — Specific, third-person, with trigger terms
4. **Write SKILL.md** — Keep under 500 lines; use `reference.md` for details
5. **Test** — Ask Cursor to do something that should trigger the skill
