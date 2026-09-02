---
name: doncheli-solid
description: Audit and refactor codebase against the 5 SOLID Object-Oriented Design principles (SRP, OCP, LSP, ISP, DIP). Activate when user mentions "SOLID", "refactor solid", "single responsibility", "dependency inversion", "open closed", "interface segregation", "liskov".
---

# Don Cheli: SOLID Design Refactoring

## Purpose
Audit existing code or evaluate new designs to ensure adherence to the 5 SOLID design principles, preventing rigid, fragile, and tightly coupled architectures.

---

## The 5 SOLID Principles Checklist

### 1. Single Responsibility Principle (SRP)
- **Check:** Does each class/module have only ONE reason to change?
- **Red Flags:** "God classes", mixing database logic with business rules or HTTP presentation, files > 300 lines.
- **Refactoring:** Extract concerns into specialized service, repository, or value objects.

### 2. Open/Closed Principle (OCP)
- **Check:** Is code open for extension but closed for modification?
- **Red Flags:** Massive `switch` or `if/else` chains checking types to alter behavior.
- **Refactoring:** Use polymorphism, strategy patterns, or handler registries.

### 3. Liskov Substitution Principle (LSP)
- **Check:** Can derived classes/implementations be substituted for their base types without altering correctness?
- **Red Flags:** Subclasses throwing `NotImplementedError`, overriding methods to do nothing, or altering base expectations.
- **Refactoring:** Favor composition over inheritance or refine interface contracts.

### 4. Interface Segregation Principle (ISP)
- **Check:** Are interfaces small, focused, and client-specific?
- **Red Flags:** Large interfaces with 10+ methods where callers only use 1 or 2.
- **Refactoring:** Split fat interfaces into fine-grained role interfaces.

### 5. Dependency Inversion Principle (DIP)
- **Check:** Do high-level modules depend on abstractions (interfaces) rather than low-level concrete implementations?
- **Red Flags:** Instantiating concrete infrastructure classes directly (`new PostgresRepository()`) inside business logic.
- **Refactoring:** Inject dependencies via constructors using interfaces/abstract ports.

---

## Execution Workflow

1. **Analyze Codebase:** Read target module and evaluate against the 5 SOLID principles.
2. **Identify Violations:** List concrete violations with file, line range, and severity.
3. **Formulate Refactoring Plan:** Create an incremental, backwards-compatible refactoring blueprint.
4. **TDD Execution:** Write failing tests for new abstractions, refactor code, and verify all tests pass.
