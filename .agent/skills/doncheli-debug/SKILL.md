---
name: doncheli-debug
description: Execute systematic root-cause debugging for complex failures using reproduction tests, log inspection, and empirical evidence before editing code. Activate when user mentions "debug", "depurar", "bug", "error", "fix failure", "root cause", "500 error", "crash".
---

# Don Cheli: Systematic Root-Cause Debugging

## Purpose
Enforce **Iron Law #2 (Root Cause First)**. Prohibit superficial symptom patches, swallowed exceptions, or guessing code fixes without empirical evidence.

---

## The 5-Step Debugging Protocol

### Step 1: Formulate Explicit Hypothesis
- State what you suspect is broken, why it fails, and what evidence supports or refutes it.
- Never edit production code before formulating an explicit hypothesis.

### Step 2: Reproduce with Automated Test (RED)
- Write an isolated unit or integration test that reproduces the exact failure.
- Run the test and confirm it fails with the expected error message or stack trace.

### Step 3: Inspect Empirical Evidence
- Fetch full stack traces, server logs, or execution metrics.
- Trace upstream data providers and verify null/uninitialized states.

### Step 4: Implement Minimal Root-Cause Fix (GREEN)
- Apply the targeted fix at the true root cause (not a wrapper `try/except` or empty fallback).
- Re-run the reproduction test to confirm it passes.

### Step 5: Verify & Regression Check
- Run the full test suite to ensure zero regressions in related modules.
- Record findings in `.dc/findings.md`.
