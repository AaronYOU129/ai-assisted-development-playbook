# Shared Agent Instructions

## Required Reading

Before starting any task, read:

* `docs/coding-principles.md`
* `docs/ai-assisted-development-workflow.md`

Follow the applicable principles and workflow throughout the task.

## Verification Before Completion

Before declaring a non-trivial coding task complete:

1. Identify the acceptance criteria from the specification.
2. Run the repository's relevant tests, linting, type checks, and
   build commands.
3. Verify each acceptance criterion against the actual system state.
4. Test both expected behavior and important failure or edge cases.
5. Review the final diff for:
   - unrelated changes;
   - incomplete implementation;
   - incorrect assumptions;
   - regressions;
   - unnecessary complexity;
   - security or compatibility risks.
6. Do not treat passing tests as sufficient when the tests do not
   cover the complete specification.
7. Report:
   - checks performed;
   - commands executed and their results;
   - acceptance criteria verified;
   - anything that remains unverified.

Never claim that a task is complete when required verification could
not be performed.

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


At the end of a task, provide a concise report containing:

1. What changed
2. Which files changed
3. What was verified, including:
   - commands or checks performed;
   - their results;
   - acceptance criteria confirmed.
4. Any assumptions, limitations, or items that remain unverified
5. The next relevant step, only if one remains

Code generation alone does not constitute completion. A task is complete
only when the requirements are satisfied and the result has been verified.At the end of a task, provide a concise report containing:

## Completion Report
1. What changed
2. Which files changed
3. What was verified, including:
   - commands or checks performed;
   - their results;
   - acceptance criteria confirmed.
4. Any assumptions, limitations, or items that remain unverified
5. The next relevant step, only if one remains

Code generation alone does not constitute completion. A task is complete
only when the requirements are satisfied and the result has been verified.
