# Tools

Scripts, CLIs, and utilities for AI builders and data product managers.

## Purpose

This directory holds:

- **Project scripts** — Reusable helpers for data, specs, or workflows
- **Quick reference** — Commands you’ll use often with Cursor and AI tooling

For a full index of skills, MCPs, and discovery tools, see [knowledge/04-tools-skills-mcps.md](../knowledge/04-tools-skills-mcps.md).

---

## Essential Commands

### Skills (open ecosystem)

```bash
npx skills find [query]              # Search for skills
npx skills add <owner/repo@skill>    # Install a skill
npx skills check                     # Check for updates
npx skills update                    # Update installed skills
```

Browse: https://skills.sh/

### Git

```bash
git status
git checkout -b feature/my-feature
git add . && git commit -m "feat: description"
git push origin feature/my-feature
```

See [knowledge/03-git-workflow.md](../knowledge/03-git-workflow.md) for details.

---

## Project Scripts

*(Add project-specific scripts here as you create them.)*

| Script | Description |
|--------|-------------|
| — | — |

---

## Adding Tools

When you add a script or utility:

1. Put it in `tools/` (or a subdirectory like `tools/scripts/`)
2. Add a row to the Project Scripts table above
3. Include a short usage comment at the top of the file
