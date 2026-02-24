# Git Workflow

A practical guide to branches, commits, and collaboration with Git.

## Setup and First Branch (Walk-through)

Follow these steps when joining a project or starting work on a new repo.

### 1. Initial Git setup (one-time)

If you haven't configured Git yet:

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

### 2. Clone the repository

```bash
git clone <repo-url>
cd <repo-name>
```

### 3. Request branch permissions

**Important:** Before creating branches in a repo you don't own, ask the repo owner (e.g. Haya, Dev, or whoever maintains it) for permission to create branches. Some repos restrict who can push new branches. Get the go-ahead before you start working.

### 4. Start working on a branch

```bash
git checkout main
git pull origin main
git checkout -b feature/my-feature
```

You're now on your branch and ready to make changes.

---

## Core Concepts

- **Repository (repo)** — A project’s history and files
- **Branch** — A parallel line of work (e.g. `main`, `feature/add-reports`)
- **Commit** — A snapshot of changes with a message
- **Remote** — A shared copy of the repo (e.g. on GitHub)

## Essential Commands

### Check Status
```bash
git status          # What’s changed? What’s staged?
git log --oneline   # Recent commits
```

### Create a Branch
```bash
git branch feature/my-feature    # Create branch
git checkout feature/my-feature  # Switch to it

# Or in one step:
git checkout -b feature/my-feature
```

### Stage and Commit
```bash
git add file.txt           # Stage one file
git add .                  # Stage all changes
git commit -m "feat: add report export"
```

### Push and Pull
```bash
git push origin feature/my-feature   # Push your branch
git pull origin main                 # Update from main
```

## Branch Naming

Common conventions:

| Prefix | Use |
|--------|-----|
| `feature/` | New features |
| `fix/` | Bug fixes |
| `docs/` | Documentation only |
| `refactor/` | Code restructuring |

Examples: `feature/add-dashboard`, `fix/date-formatting`, `docs/update-readme`

## Commit Messages

### Format
```
<type>: <short description>

[Optional longer description]
```

### Types
- `feat` — New feature
- `fix` — Bug fix
- `docs` — Documentation
- `refactor` — Code change, no behavior change
- `test` — Tests
- `chore` — Maintenance (deps, config)

### Examples
```
feat(reports): add CSV export
fix(dates): correct timezone in dashboard
docs: update API section in README
```

## Typical Workflow

1. **Start from latest main**
   ```bash
   git checkout main
   git pull origin main
   ```

2. **Create a branch**
   ```bash
   git checkout -b feature/my-change
   ```

3. **Make changes, stage, commit**
   ```bash
   git add .
   git commit -m "feat: describe your change"
   ```

4. **Push and open a PR**
   ```bash
   git push origin feature/my-change
   ```
   Then create a Pull Request on GitHub.

5. **After merge** — Switch back to main and pull
   ```bash
   git checkout main
   git pull origin main
   ```

## Undoing Things

| Situation | Command |
|-----------|---------|
| Unstage a file | `git restore --staged file.txt` |
| Discard changes in a file | `git restore file.txt` |
| Undo last commit (keep changes) | `git reset --soft HEAD~1` |
| Undo last commit (discard changes) | `git reset --hard HEAD~1` |

**Caution:** `--hard` permanently discards changes.

## Cursor + Git

- **Ask Cursor** to suggest commit messages from your diff
- **Use branches** to try ideas without affecting `main`
- **Review diffs** in Cursor before committing
- **Rules and skills** can guide commit message format or PR review

## Quick Reference

| Task | Command |
|------|---------|
| See branches | `git branch -a` |
| Switch branch | `git checkout <branch>` |
| Merge branch into current | `git merge <branch>` |
| See remote URL | `git remote -v` |
| Clone a repo | `git clone <url>` |
