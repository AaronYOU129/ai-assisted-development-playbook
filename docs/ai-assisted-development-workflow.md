# AI-Assisted Development Workflow

AI can accelerate implementation, but reliable development still requires explicit requirements, sound design, controlled execution, and careful verification.

This workflow keeps important information in project files rather than relying only on conversational context.

```text
Requirements → Design → Task Decomposition → Implementation → Verification
```

These stages are sequential but iterative. If implementation or verification reveals a problem, return to the earliest affected stage and update the relevant files.

## Stage 1 — Requirements Definition

Before designing or implementing a task, define:

* **Goal:** What problem needs to be solved?
* **Inputs:** What data, files, parameters, or user actions are required?
* **Outputs:** What artifacts or behaviors should be produced?
* **Constraints:** What technical, operational, privacy, or methodological limits apply?
* **High-Level Steps:** What is the expected workflow?
* **Acceptance Criteria:** How will completion be verified?

The AI should ask for clarification when an ambiguity could materially change the result.

For minor details, the AI may make assumptions only when they are:

* Safe
* Reversible
* Clearly stated

Requirements should be recorded in:

```text
requirements.md
```

Implementation should not begin until the acceptance criteria are sufficiently clear.

## Stage 2 — Design

Translate the requirements into a high-level architecture and detailed implementation plan.

The design should define:

* Module responsibilities
* Inputs and outputs for each module
* Interfaces between modules
* Data flow
* Dependencies
* Error-handling strategy
* Testing and validation strategy

Two principles guide the design:

1. Modules should remain as independent and independently testable as practical.
2. Important decisions should be recorded in files rather than kept only in an AI conversation.

Design decisions should be recorded in:

```text
design.md
```

Material changes to the design should be documented before or alongside implementation.

## Stage 3 — Task Decomposition

Break each module into the smallest independently verifiable tasks.

Each module should have its own task file:

```text
tasks/
├── data-processing.md
├── estimation.md
└── reporting.md
```

Each task should specify:

* Goal
* Inputs
* Outputs
* Dependencies
* Files allowed to change
* Acceptance criteria
* Verification commands

Use checklists to track implementation:

```markdown
- [ ] Define the module interface
- [ ] Implement the core behavior
- [ ] Validate inputs
- [ ] Handle edge cases
- [ ] Add tests
- [ ] Run quality checks
- [ ] Update documentation
```

Track module-level progress in:

```text
progress.md
```

A task should be small enough to implement and verify within a focused AI session, but large enough to produce meaningful behavior.

## Stage 4 — Implementation

Implementation should be driven by `requirements.md`, `design.md`, `progress.md`, and the relevant module task file.

At the beginning of an implementation session, the AI should:

1. Read the relevant project files.
2. Identify the next incomplete task.
3. Inspect the existing implementation and tests.
4. Confirm the files that may be modified.
5. Identify material ambiguities before writing code.

During implementation, the AI should:

* Make the smallest change that fully satisfies the task.
* Follow the project’s coding principles.
* Avoid modifying unrelated files.
* Preserve established interfaces unless a change is required.
* Add or update tests with the implementation.
* Record material assumptions and design changes.

After implementation, the AI should:

1. Run the relevant tests and quality checks.
2. Compare the result with the acceptance criteria.
3. Update the module checklist.
4. Update `progress.md`.
5. Report completed work and remaining limitations.

## Single-Agent and Multi-Agent Work

Use a single agent when:

* The project is small.
* Tasks are tightly coupled.
* Several tasks modify the same files.
* Coordination would cost more than parallel execution would save.

Use multiple agents only when modules are sufficiently independent.

In a multi-agent workflow:

* The **main agent** manages requirements, interfaces, dependencies, integration, and overall progress.
* **Sub-agents** implement and test clearly bounded modules.
* Each sub-agent receives an explicit goal, allowed files, acceptance criteria, and verification commands.
* Agents should not modify overlapping files concurrently unless their work has been explicitly coordinated.
* The main agent must review and verify the integrated result.

Sub-agents reduce context size, but they do not remove the need for integration review.

## Stage 5 — Verification

A task is complete only when its result has been verified. Code generation alone does not constitute completion.

Verification should include:

* Running relevant automated tests
* Checking important outputs manually when appropriate
* Confirming that acceptance criteria are satisfied
* Reviewing error handling and edge cases
* Confirming that documentation remains accurate
* Checking that no credentials or sensitive data were introduced

For Python projects, the default quality checks are:

```bash
pytest
mypy .
ruff check .
ruff format --check .
```

These commands should be adapted to the project’s actual technology stack.

If a check cannot be run, the AI must state:

* Which check was not run
* Why it could not be run
* What remains unverified

If verification fails, record the failure, update the relevant task, and continue from the smallest affected unit.

## Context Management

To keep AI sessions focused:

* Store requirements, design decisions, assumptions, and progress in files.
* Do not rely on conversational memory for critical project information.
* Read only the files relevant to the current task.
* Keep task boundaries explicit.
* Update project files when decisions change.
* Use `decision-log.md` for decisions that materially affect architecture, methodology, or results.

## Prompting Principle

A task prompt should identify:

* The goal
* The relevant project files
* The files allowed to change
* The constraints
* The acceptance criteria
* The required tests and quality checks
* The expected completion report

The AI should ask questions when unresolved ambiguity could materially affect the result. It may proceed with minor, safe, and reversible assumptions only when those assumptions are explicitly documented.

## Completion Principle

AI-assisted development is complete only when:

```text
The requirements are satisfied,
the implementation is understandable,
the tests pass,
and the result has been verified.
```
