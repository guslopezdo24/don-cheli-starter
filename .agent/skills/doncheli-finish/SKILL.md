---
name: doncheli-finish
description: Perform rigorous pre-completion verification, terminal test evidence checks, worktree cleanup, and final integration when completing a feature branch or TDD task. Activate when user mentions "finish branch", "complete task", "done", "merge feature", "verify before completion", "final review".
---

# Don Cheli: Branch & Feature Finalization

## Purpose
Enforce **Iron Law #3 (Evidence Before Assertions)** before marking a feature or development branch as complete.

---

## 4-Step Finalization Protocol

### 1. Verification of Empirical Evidence
- Execute full test suite (`npm test`, `pytest`, `cargo test`, etc.).
- Verify **zero test failures** and **coverage ≥ 85%**.
- Check for zero remaining stubs (`// TODO`, `throw new Error('not implemented')`).

### 2. Diff & Quality Audit
- Run `@doncheli-review` to ensure 7-dimension review clean status.
- Ensure all intermediate scratch files or `.tmp` files are removed.

### 3. State & Ledger Update
- Update `.dc/status.md` to `Phase: Complete`.
- Update `.dc/progress.md` marking all tasks completed.
- Log any architectural rulings or key findings in `.dc/findings.md`.

### 4. Integration & Cleanup
- If a `git worktree` was used, remove the worktree.
- Present final clean git commit history or PR summary.
