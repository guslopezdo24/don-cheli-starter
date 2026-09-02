# Don Cheli — SDD Project Template 🏗️

[![Don Cheli Main Repo](https://img.shields.io/badge/Main_Repo-don--cheli--sdd-6c5ce7?style=for-the-badge&logo=github)](https://github.com/doncheli/don-cheli-sdd)
[![Specification Driven Development](https://img.shields.io/badge/Methodology-SDD_%2B_TDD-brightgreen?style=for-the-badge)](https://github.com/doncheli/don-cheli-sdd)
[![License: Apache 2.0](https://img.shields.io/badge/License-Apache_2.0-blue?style=for-the-badge)](LICENSE)

> **Stop guessing. Start engineering.**  
> Official agnostic starter template to kickstart software projects using **Specification-Driven Development (SDD)** with AI assistance (Antigravity, Cursor, Claude Code, OpenCode, Codex, Windsurf, Roo Code).

---

## 📌 Table of Contents

- [What is Don Cheli SDD?](#-what-is-don-cheli-sdd)
- [Why SDD over Traditional AI Coding?](#-why-sdd-over-traditional-ai-coding)
- [The 3 Iron Laws (Non-Negotiable)](#-the-3-iron-laws-non-negotiable)
- [How the Framework Works (The 7-Phase Pipeline)](#-how-the-framework-works-the-7-phase-pipeline)
- [Complexity Auto-Detection (Levels 0 to 4)](#-complexity-auto-detection-levels-0-to-4)
- [Semantic Skills & SuperPowers Capabilities](#-semantic-skills--superpowers-capabilities)
- [Project State Persistence (`.dc/`)](#-project-state-persistence-dc)
- [🚀 Quickstart & Setup](#-quickstart--setup)
- [💬 Natural Conversation vs. Explicit Skills](#-natural-conversation-vs-explicit-skills)
- [💬 Interactive Example Workflows (Steroids Mode)](#-interactive-example-workflows-steroids-mode)
  - [Workflow A: New Feature (Full SDD Pipeline)](#workflow-a-new-feature-full-sdd-pipeline)
  - [Workflow B: Root-Cause Bug Fix (Zero Symptom Patching)](#workflow-b-root-cause-bug-fix-zero-symptom-patching)
  - [Workflow C: Pre-Mortem & Architecture Debate](#workflow-c-pre-mortem--architecture-debate)
  - [Workflow D: OWASP Security Audit & Hardening](#workflow-d-owasp-security-audit--hardening)
  - [Workflow E: Legacy Code Distillation & Refactoring](#workflow-e-legacy-code-distillation--refactoring)
  - [Workflow F: Isolated Subagent & Worktree Execution](#workflow-f-isolated-subagent--worktree-execution)
- [🔗 Reference & Community](#-reference--community)

---

## 💡 What is Don Cheli SDD?

**Don Cheli SDD** is an open-source Specification-Driven Development framework designed for AI-assisted coding.

Instead of prompting an AI agent to write code blindly (which leads to hallucinated functions, untested logic, architectural drift, and silent bugs), **Don Cheli enforces intermediate engineering checkpoints**:

1. **Declarative Specifications:** Features are specified in Gherkin BDD (`.feature`) files *before* code is touched.
2. **Technical Blueprints:** Architectures, data schemas (DBML), and API contracts are planned and agreed upon up front.
3. **Strict Test-Driven Development (TDD):** Every line of code is produced through a strict `RED → GREEN → REFACTOR` cycle.
4. **Automated Quality Gates:** Progress is gated by quality criteria (coverage ≥ 85%, 0 stubs, 7-dimension code review).

This template repository is derived from the core framework at **[doncheli/don-cheli-sdd](https://github.com/doncheli/don-cheli-sdd)**.

---

## ⚡ Why SDD over Traditional AI Coding?

| Traditional AI Coding | Don Cheli SDD |
| :--- | :--- |
| **Vibe coding:** Prompts lead directly to code changes. | **Specification first:** Code is written only after BDD specs are accepted. |
| **No test guarantee:** Tests are added as an afterthought (or skipped). | **TDD as Law:** Code without failing tests first is rejected. |
| **Context loss:** The agent forgets context in long sessions. | **Persistent State & Subagent Isolation:** State lives in versioned `.dc/` Markdown files. |
| **Superficial fixes:** AI patches symptoms with try/except wrappers. | **Root Cause First:** AI must isolate the root cause before patching (`doncheli-debug`). |
| **Tool Lock-in:** Tied to one specific IDE or CLI tool. | **Agnostic & Universal:** Reads universal `AGENTS.md` and `.agent/skills/`. |

---

## ⚖️ The 3 Iron Laws (Non-Negotiable)

These three laws are embedded in `AGENTS.md` and enforced across all phases:

```
┌────────────────────────────────────────────────────────────────────────┐
│                          THE 3 IRON LAWS                               │
├────────────────────────────────────────────────────────────────────────┤
│ 1. TDD IS LAW (RED → GREEN → REFACTOR)                                 │
│    Never write production code without a failing unit test first.      │
│    Zero TODO stubs or empty fallback functions in production code.     │
├────────────────────────────────────────────────────────────────────────┤
│ 2. ROOT CAUSE FIRST (DEBUGGING PROTOCOL)                               │
│    Never apply superficial symptom patches or swallow exceptions.       │
│    Isolate the root cause using empirical log evidence first.          │
├────────────────────────────────────────────────────────────────────────┤
│ 3. EVIDENCE BEFORE ASSERTIONS (VERIFICATION PROTOCOL)                  │
│    Never claim code works without showing real test execution output.  │
│    Coverage must be ≥ 85% on all new business logic.                   │
└────────────────────────────────────────────────────────────────────────┘
```

---

## 🔄 How the Framework Works (The 7-Phase Pipeline)

When assigned a task, the AI agent navigates through 7 disciplined phases:

```
 ┌──────────┐      ┌──────────┐      ┌────────────┐      ┌───────────┐
 │ Specify  │ ───> │ Clarify  │ ───> │ Tech Plan  │ ───> │ Breakdown │
 └──────────┘      └──────────┘      └────────────┘      └───────────┘
                                                               │
 ┌──────────┐      ┌──────────┐                          │
 │  Verify  │ <─── │  Review  │ <────────────────────────┘
 └──────────┘      └──────────┘
```

1. **Specify:** Converts natural language requests into Gherkin BDD `.feature` files with prioritized scenarios (P1/P2/P3+) and DBML entity schemas.
2. **Clarify:** Evaluates specs for edge cases, missing sad paths, and ambiguities (`[NEEDS CLARIFICATION]`).
3. **Tech Plan:** Generates technical blueprint (`.dc/plan.md`) covering service boundaries, DB schema, and API contracts.
4. **Breakdown:** Divides the blueprint into atomic, ordered TDD tasks in `.dc/progress.md`.
5. **Implement:** Executes TDD task-by-task: Write test (RED) → Write minimum code (GREEN) → Refactor (REFACTOR).
6. **Review:** Performs a 7-dimension adversarial code review analyzing Correctness, Security, Architecture, Performance, Tests, Style, and Diff Cleanliness.
7. **Verify:** Runs full test suite, linter, and checks for zero regression before completing the task.

---

## 🎚️ Complexity Auto-Detection (Levels 0 to 4)

Not every task needs the full pipeline. The framework automatically adapts rigor to scope:

* **Level 0 (Atomic):** 1 file, <30 mins ➔ Skip heavy specs; run `implement` → `verify`.
* **Level P (PoC):** Proof of Concept ➔ Timeboxed 2–4h with relaxed coverage.
* **Level 1 (Micro):** 1–3 files ➔ Lightweight spec → `implement` → `review`.
* **Level 2 (Standard - Default):** Multi-file / multi-day ➔ Full 7-phase pipeline.
* **Level 3 & 4 (Complex/Product):** Multi-module / system ➔ Full pipeline + ADR in `.dc/memory/decisions/`.

---

## 🧠 Semantic Skills & SuperPowers Capabilities

The template includes 32 pre-configured skills under `.agent/skills/` built on the open **[agentskills.io](https://agentskills.io)** standard.

AI agents discover and activate these skills automatically via natural conversation:

### 🛠️ Core SDD & Execution Skills
* `doncheli-spec` — Generate Gherkin BDD specs and DBML schemas.
* `doncheli-plan` — Create technical blueprints and architecture designs.
* `doncheli-implement` — TDD execution engine (RED → GREEN → REFACTOR).
* `doncheli-review` — 7-dimension adversarial peer review.
* `doncheli-security` — OWASP Top 10 static security audit.
* `doncheli-subagent` — Dispatch fresh subagents per task to prevent context bloat.
* `doncheli-debug` — Systematic root-cause debugging (hypothesis → reproduction test → fix).
* `doncheli-worktree` — Execute tasks in isolated git worktrees without touching active working branch.
* `doncheli-finish` — Pre-completion empirical verification & clean branch integration.

### 🏛️ Architecture & Reasoning
* `doncheli-solid` — Audit and refactor codebase against the 5 SOLID principles.
* `doncheli-reasoning` — Apply 15 mental models (Pre-mortem, 5-Whys, Pareto, First Principles, Inversion, etc.).
* `doncheli-debate` — Multi-role debate (CPO vs Architect vs QA vs Security).
* `doncheli-tech-panel` — Senior dev experts table consultation.
* `doncheli-api-contract` — REST/GraphQL contract design with retries & circuit breakers.
* `doncheli-migrate` — Technology stack migration & wave planning.

### 📊 Quality & Governance
* `doncheli-estimate` — Multi-model effort estimation (COCOMO, Function Points, Poker AI).
* `doncheli-drift` — Detect divergence between `.dc/specs/` and actual codebase.
* `doncheli-tech-debt` — Identify, quantify, and prioritize technical debt.
* `doncheli-changelog` — Auto-generate release changelogs from git history.
* `doncheli-context-health` — Analyze and optimize LLM context window usage.

---

## 💬 Natural Conversation vs. Explicit Skills

> **Is using `@doncheli-implement` or `@` notation required?**  
> **NO!** You can speak to your AI agent in 100% natural, plain language.

Agents automatically select skills based on semantic intent. Both styles work identically:

| Approach | Prompt Example | How It Works |
| :--- | :--- | :--- |
| **1. Pure Natural Language** *(Recommended)* | `"Let's build a rate limiter middleware for our REST API using TDD."` | The agent automatically matches your intent to `doncheli-spec` and `doncheli-implement` skills. |
| **2. Explicit Skill Mention** *(Optional)* | `"Let's write unit tests and code for this feature using @doncheli-implement."` | Explicitly pinpoints a specific skill if you want 100% explicit control. |

---

## 💾 Project State Persistence (`.dc/`)

Project state is stored as versionable Markdown files inside `.dc/`:

```text
.dc/
├── config.yaml          # Framework config (locale: en, rigor: standard)
├── status.md            # Active task, current phase, and blockers
├── plan.md              # Active technical blueprint & architecture
├── progress.md          # TDD implementation checklist
├── findings.md          # Refactoring notes & discoveries log
├── specs/               # Gherkin BDD feature specifications (.feature)
├── blueprints/          # Architecture diagrams & schematics
└── memory/decisions/    # Architecture Decision Records (ADRs)
```

---

## 🚀 Quickstart & Setup

### Option 1: Use GitHub Template (Recommended)
1. Click **"Use this template"** ➔ **"Create a new repository"** at the top right of this GitHub repo.
2. Clone your newly created repository locally.
3. Open the folder in your favorite AI coding tool (Google Antigravity, Cursor, VS Code + Claude Code, OpenCode, Windsurf, etc.).

### Option 2: Clone via `degit` or `git`
```bash
# Clone without git history using degit
npx degit doncheli/don-cheli-starter my-project
cd my-project

# Or standard git clone
git clone https://github.com/doncheli/don-cheli-starter.git my-project
cd my-project
rm -rf .git && git init
```

---

## 💬 Interactive Example Workflows (Steroids Mode)

Simply talk to your AI agent using any of these natural conversational prompt patterns:

---

### Workflow A: New Feature (Full SDD Pipeline)
```text
Prompt 1 (Specify): "We need to implement a Redis-based rate limiter middleware (100 req/min). Specify this first."
Prompt 2 (Plan):    "Create the technical blueprint and API contract."
Prompt 3 (Implement): "Execute the TDD tasks from .dc/progress.md. Write failing unit tests first!"
Prompt 4 (Review):   "Run a 7-dimension code review and verify all quality gates pass."
```

---

### Workflow B: Root-Cause Bug Fix (Zero Symptom Patching)
```text
Prompt:
"Users report a 500 error when uploading files larger than 10MB during peak hours. Investigate the root cause from logs, write a failing unit test to reproduce the bug (RED), and then fix it cleanly (GREEN)."
```

---

### Workflow C: Pre-Mortem & Architecture Debate
```text
Prompt:
"We are considering migrating our event log from PostgreSQL to DynamoDB. Run a pre-mortem to anticipate potential failures, and run an adversarial debate between a Cloud Architect, a DBA, and a QA Lead."
```

---

### Workflow D: OWASP Security Audit & Hardening
```text
Prompt:
"Perform an OWASP Top 10 security audit on our authentication and payment handler modules. Identify any injection risks, broken access controls, or missing rate limits."
```

---

### Workflow E: Legacy Code Distillation & Refactoring
```text
Prompt:
"Analyze the legacy billing module in `src/legacy/billing.js`. Extract its behavioral Gherkin specifications, and generate a TDD refactoring plan to rewrite it using Clean Architecture."
```

---

### Workflow F: Isolated Subagent & Worktree Execution
```text
Prompt:
"Execute the implementation plan for our payment processing module in a dedicated git worktree, dispatching isolated subagents per task to keep our main working tree clean."
```

---

## 🔗 Reference & Community

* **Main Project Repository:** [github.com/doncheli/don-cheli-sdd](https://github.com/doncheli/don-cheli-sdd)
* **Official Website & Docs:** [doncheli.tv](https://doncheli.tv)
* **Open Standard:** [agentskills.io](https://agentskills.io)
* **License:** [Apache 2.0](LICENSE) — Copyright 2026 Jose Luis Oronoz Troconis ([@DonCheli](https://github.com/doncheli))

---

<p align="center">
  <sub>Made with ❤️ for precision AI software engineering — Don Cheli SDD Framework</sub>
</p>
