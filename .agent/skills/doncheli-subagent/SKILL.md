---
name: doncheli-subagent
description: Execute complex TDD implementation plans by dispatching isolated subagents per task to prevent context pollution and maximize execution quality. Activate when user mentions "subagent", "subagente", "parallel agents", "dispatch agent", "isolated context".
---

# Don Cheli: Subagent-Driven Execution

## Purpose
Prevent context degradation and token bloat during multi-task implementations by delegating individual TDD tasks to fresh subagents with strictly isolated task contexts.

---

## Core Principle
`Fresh Subagent per Task` + `Task-Scoped Review` + `Main Controller Synthesis` = **High Quality & Fast Iteration**.

---

## Dispatching Rules

1. **Context Isolation:** Never pass the full conversation history or the entire project plan to a subagent. Pass only:
   - The specific task brief (`.dc/progress.md` task item).
   - Target files and interfaces.
   - Relevant project constraints from `AGENTS.md`.
2. **Subagent Role:** Subagents act as implementers. They follow the TDD cycle (`RED → GREEN → REFACTOR`), write tests first, implement code, and run tests.
3. **No Nested Subagents:** Implementer subagents must never launch their own subagents.
4. **Execution Protocol:**
   - **Step 1:** Controller creates a minimal task brief.
   - **Step 2:** Controller dispatches a fresh implementer subagent.
   - **Step 3:** Implementer executes TDD (RED → GREEN → REFACTOR) and returns unit test evidence.
   - **Step 4:** Controller dispatches a task reviewer subagent to audit diff and spec compliance.
   - **Step 5:** Controller updates `.dc/progress.md` ledger and proceeds to next task.
