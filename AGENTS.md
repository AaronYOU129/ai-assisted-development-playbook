# Shared Agent Instructions

## Required Reading

Before starting any task, read:

* `docs/coding-principles.md`
* `docs/ai-assisted-development-workflow.md`

Follow the applicable principles and workflow throughout the task.

For non-trivial projects, also read the following files when they exist:

* `requirements.md`
* `design.md`
* `progress.md`
* The relevant file under `tasks/`

Do not rely on conversational memory when the required information is available in project files.

## Repository Purpose

This repository provides a reusable playbook for human-centered coding and structured AI-assisted development.

Its goals are to help people and AI agents produce code that is:

* Readable
* Modular
* Testable
* Maintainable
* Reproducible

## Before Starting Work

Before making changes:

1. Identify the goal, inputs, outputs, constraints, and acceptance criteria.
2. Read the relevant project documentation.
3. Inspect the existing implementation and tests.
4. Identify the files that may need to change.
5. Ask for clarification when an ambiguity could materially affect the result.
6. State any minor, safe, and reversible assumptions explicitly.

For substantial new features, do not begin implementation until the requirements and design are sufficiently clear.

Small and reversible changes may proceed without a separate design document when the intended behavior is unambiguous.

## Implementation Rules

When implementing a task:

* Make the smallest change that fully satisfies the requirements.
* Do not modify unrelated files.
* Preserve established interfaces unless a change is required.
* Keep high-level workflow separate from implementation details.
* Give each function one clear responsibility.
* Prefer explicit, readable code over clever shortcuts.
* Use early returns to reduce unnecessary nesting.
* Handle invalid inputs and edge cases explicitly.
* Use consistent, descriptive, and searchable names.
* Add or update tests alongside behavioral changes.
* Record material assumptions, limitations, and design changes.
* Do not introduce a new dependency unless it provides clear value.
* Never commit credentials, API keys, private data, or confidential outputs.

Follow the detailed standards in `docs/coding-principles.md`.

## Task and Progress Management

When `progress.md` and module task files are present:

* Work on the next incomplete task unless instructed otherwise.
* Keep each task independently verifiable.
* Respect the list of files allowed to change.
* Update the relevant checklist after verification.
* Update `progress.md` when module-level status changes.
* Do not mark a task complete before its acceptance criteria are satisfied.

Use `decision-log.md` when a decision materially affects architecture, methodology, interfaces, or results.

## Agent Coordination

Use a single agent for small or tightly coupled work.

Use sub-agents only when tasks are sufficiently independent and parallel work provides a clear benefit.

When using sub-agents:

* Give each sub-agent a bounded goal.
* Specify its inputs, outputs, allowed files, and acceptance criteria.
* Prevent agents from modifying overlapping files concurrently.
* Keep integration responsibility with the main agent.
* Review and verify the combined result before completion.

Follow the coordination rules in `docs/ai-assisted-development-workflow.md`.

## Source-of-Truth Rules

For this playbook repository:

* `docs/coding-principles.md` defines the coding standards.
* `docs/ai-assisted-development-workflow.md` defines the development process.
* `templates/` contains reusable project artifacts.
* `examples/` demonstrates how the templates should be used.
* `README.md` introduces and navigates the repository.

If files conflict, resolve the conflict in the relevant source-of-truth document before updating dependent files.

Do not duplicate the same principle across multiple files unless duplication is necessary for a standalone template.

## Verification

A task is complete only after its result has been verified.

Before declaring completion:

* Run the relevant automated tests.
* Run the project’s type, lint, and formatting checks.
* Compare the result with the acceptance criteria.
* Review important edge cases and failure modes.
* Confirm that documentation remains accurate.
* Confirm that no unrelated files were changed.
* Confirm that no sensitive information was introduced.
* Update progress and task files when applicable.
* Report what was verified.
* Explain anything that remains unverified.

For Python projects, use the following default quality checks when they are configured:

```bash
pytest
mypy .
ruff check .
ruff format --check .
```

Adapt these commands to the project’s actual technology stack.

Do not claim that a check passed unless it was actually run successfully.

If a check cannot be run, report:

* Which check was not run
* Why it could not be run
* What remains unverified

## Completion Report

At the end of a task, provide a concise report containing:

1. What changed
2. Which files changed
3. What was verified
4. Any assumptions or limitations
5. The next relevant step, if one remains

Code generation alone does not constitute completion. A task is complete only when the requirements are satisfied and the result has been verified.
