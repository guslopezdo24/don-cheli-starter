---
name: doncheli-worktree
description: Create and manage isolated git worktrees to execute experiments, feature development, or autonomous TDD tasks without polluting or breaking the user's active working branch. Activate when user mentions "worktree", "isolate branch", "workspace isolation", "git worktree", "sandbox branch".
---

# Don Cheli: Worktree Isolation

## Purpose
Isolate complex tasks or autonomous TDD runs in dedicated `git worktrees`. This ensures the main working tree remains 100% clean and working at all times.

---

## Workflow

### 1. Create Worktree
```bash
git worktree add -b sdd/<feature-name> .dc/worktrees/<feature-name> main
```

### 2. Execute Task in Isolated Path
- All file edits, test executions, and intermediate TDD commits occur inside `.dc/worktrees/<feature-name>/`.
- The user's main working tree is completely untouched during the implementation process.

### 3. Cleanup & Merge
- Once all Quality Gates pass, merge the clean commits into `main` (or create PR).
- Delete the worktree directory:
```bash
git worktree remove .dc/worktrees/<feature-name>
git branch -d sdd/<feature-name>
```
