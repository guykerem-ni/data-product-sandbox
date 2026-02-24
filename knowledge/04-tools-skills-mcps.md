# Tools, Skills & MCPs for AI Builders & Data Product Managers

A curated index of capabilities that help AI builders and data product managers work effectively with Cursor and AI-assisted workflows.

---

## Overview

| Category | Purpose |
|----------|---------|
| **Skills** | Reusable workflows the AI follows for specific tasks (reviews, planning, debugging) |
| **MCPs** | External integrations (browser, Figma) that extend what the AI can access |
| **Tools** | CLIs and commands to discover, install, and manage capabilities |

---

## Skills

Skills are instructions the AI loads when your request matches their description. See [02-cursor-skills.md](02-cursor-skills.md) for how they work.

### Planning & Execution

| Skill | When to Use |
|-------|-------------|
| **Writing Plans** | You have a spec or requirements; need a structured implementation plan before coding |
| **Executing Plans** | You have a written plan and want to execute it step-by-step with review checkpoints |
| **Brainstorming** | Before any creative work — features, components, design — to explore intent and requirements |
| **Deep Reasoning** | Complex decisions, ambiguous tradeoffs, or when you say "think this through carefully" |
| **Context-Driven Development** | Setting up projects, creating product.md/tech-stack.md, onboarding to codebases |

### Development Workflow

| Skill | When to Use |
|-------|-------------|
| **Test-Driven Development** | Implementing features or bugfixes — write tests before implementation |
| **Systematic Debugging** | Any bug, test failure, or unexpected behavior — structured diagnosis before fixes |
| **Verification Before Completion** | Before claiming work is done — run verification, confirm output, evidence before assertions |
| **Dispatching Parallel Agents** | Multiple independent tasks that can run without shared state |
| **Subagent-Driven Development** | Executing implementation plans with independent tasks in one session |
| **Using Git Worktrees** | Feature work needing isolation, or before executing implementation plans |

### Code Quality & Review

| Skill | When to Use |
|-------|-------------|
| **Requesting Code Review** | Completing tasks, major features, or before merging — verify work meets requirements |
| **Receiving Code Review** | Before implementing review feedback — verify suggestions, don't blindly apply |
| **Finishing a Development Branch** | Implementation complete, tests pass — decide merge, PR, or cleanup |

### UI/UX & Design

| Skill | When to Use |
|-------|-------------|
| **UI/UX Pro Max** | Designing, building, or fixing UI/UX — components, accessibility, responsive layout |
| **Implement Design** (Figma) | Implementing UI from Figma files — 1:1 visual fidelity |
| **Code Connect Components** (Figma) | Connecting Figma components to code components |
| **Create Design System Rules** | Generating project-specific design system rules |

### Skills & Rules Management

| Skill | When to Use |
|-------|-------------|
| **Find Skills** | "How do I do X?", "Find a skill for X", "Is there a skill that can…" |
| **Writing Skills** | Creating, editing, or verifying new skills |
| **Create Rule** | Adding Cursor rules, coding standards, project conventions |
| **Create Skill** | Authoring new Cursor skills |
| **Skill Installer** | Installing skills from curated lists or GitHub repos |

### Other Useful Skills

| Skill | When to Use |
|-------|-------------|
| **Commit and Push on Finish** | User says "commit upon conclusion" — run tests, commit, push |
| **ACT Context Check** | Before ACT implementation — load the right spec/feedback docs |
| **ACT Decision Log** | Recording significant implementation decisions for traceability |

---

## MCPs (Model Context Protocol)

MCPs connect Cursor to external tools and data sources. Descriptor files live in your project's `mcps/` folder.

### cursor-ide-browser

**Purpose:** Navigate the web, interact with pages, test frontend changes.

| Capability | Use Case |
|------------|----------|
| `browser_navigate` | Open URLs |
| `browser_snapshot` | Get page structure and element refs before interaction |
| `browser_click`, `browser_type`, `browser_fill` | Interact with elements |
| `browser_lock` / `browser_unlock` | Lock a tab before interactions, unlock when done |
| `browser_profile_start` / `browser_profile_stop` | CPU profiling for performance investigation |

**Workflow:** `browser_navigate` → `browser_lock` → interactions → `browser_unlock`

### plugin-figma-figma

**Purpose:** Connect Cursor to Figma designs.

| Capability | Use Case |
|------------|----------|
| Design inspection | Read Figma file structure, components, styles |
| Implement design | Translate Figma designs into code |
| Code Connect | Map Figma components to code components |
| Design system rules | Generate project-specific Figma-to-code conventions |

**Requires:** Figma MCP server connection.

---

## Discovery & Installation

### Finding Skills

**Open ecosystem (skills.sh):**
```bash
npx skills find [query]
npx skills add <owner/repo@skill> -g -y
```
Browse: https://skills.sh/

**Common search categories:** react, testing, deploy, docs, review, ui, workflow, git

### Installing Skills

| Source | Command / Action |
|--------|------------------|
| skills.sh | `npx skills add <package> -g -y` |
| GitHub repo | `npx skills add owner/repo@skill-name` |
| Codex curated | Use skill-installer (Codex) for openai/skills |

### Adding MCPs

MCPs are configured in Cursor settings. New MCP servers appear in your project's `mcps/` folder when enabled. Check each server's `tools/` subfolder for available tool schemas before calling them.

---

## Quick Reference: "When Should I Use…?"

| You want to… | Use |
|--------------|-----|
| Plan before coding | Writing Plans, Brainstorming |
| Execute a plan step-by-step | Executing Plans |
| Debug something | Systematic Debugging |
| Get a code review | Requesting Code Review |
| Build UI from Figma | Implement Design + Figma MCP |
| Test in a browser | cursor-ide-browser MCP |
| Find a skill for a task | Find Skills, or `npx skills find <query>` |
| Add project conventions | Create Rule |
| Create a reusable workflow | Create Skill, Writing Skills |

---

## Related

- [01-cursor-rules.md](01-cursor-rules.md) — Project conventions and AI context
- [02-cursor-skills.md](02-cursor-skills.md) — How skills work and how to create them
- [03-git-workflow.md](03-git-workflow.md) — Git basics and collaboration
