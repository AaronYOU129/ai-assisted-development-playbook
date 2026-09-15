# AI-Assisted Development Playbook

A practical playbook for building readable, testable, and reproducible software with AI coding agents.

## Why This Repository Exists

Code is written for computers to execute, but it is also written for people to read, understand, review, and maintain.

AI can accelerate software development, but generated code is not automatically readable, reliable, or reproducible. Reliable development still requires clear requirements, sound design, modular implementation, and careful verification.

This repository combines human-centered coding principles with a structured AI-assisted development workflow.

## Core Ideas

### 1. Code Should Be Easy for People to Read

Good code should make its purpose and structure clear without requiring the reader to inspect every implementation detail.

Functions should have clear responsibilities, control flow should remain simple, and names should communicate meaning.

### 2. Important Information Should Be Stored in Files

Requirements, design decisions, tasks, assumptions, and progress should not exist only inside an AI conversation.

Storing this information in files keeps AI sessions focused, reduces inconsistent assumptions, and makes the development process easier to review and reproduce.

### 3. AI-Generated Code Must Be Verified

Generating code does not mean that a task is complete.

Important behavior should be tested, quality checks should be run, and results should be evaluated against explicit acceptance criteria.

## Development Workflow

```text
Requirements → Design → Task Decomposition → Implementation → Verification
```

The workflow has five stages:

1. **Requirements:** Define the goal, inputs, outputs, constraints, steps, and acceptance criteria.
2. **Design:** Define the architecture, modules, interfaces, dependencies, and testing strategy.
3. **Task Decomposition:** Break modules into small, independently verifiable tasks.
4. **Implementation:** Implement tasks using a single agent or coordinated sub-agents.
5. **Verification:** Run tests, inspect outputs, and confirm that the acceptance criteria are satisfied.

## Repository Contents

This repository is being developed incrementally.

* [ ] Human-centered coding principles
* [ ] AI-assisted development workflow
* [ ] Requirements and design templates
* [ ] Module-task and progress templates
* [ ] Decision log template
* [ ] Example research project

The planned structure is:

```text
ai-assisted-development-playbook/
├── README.md
├── CLAUDE.md
├── LICENSE
├── CONTRIBUTING.md
├── docs/
│   ├── coding-principles.md
│   ├── ai-assisted-development-workflow.md
│   └── usage-guide.md
├── templates/
│   ├── requirements.md
│   ├── design.md
│   ├── progress.md
│   ├── decision-log.md
│   └── module-task.md
└── examples/
    └── sample-research-project/
```

## Quality Gates

For Python projects, the default quality checks are:

```bash
pytest
mypy .
ruff check .
ruff format --check .
```

Test coverage is a diagnostic tool rather than the final objective. Tests should verify meaningful behavior, edge cases, and known failure modes.

## Who This Is For

This playbook is intended for:

* Researchers writing data-processing and estimation pipelines
* Developers using Claude Code or other AI coding agents
* People who want AI-generated code to remain readable and maintainable
* Teams that need explicit requirements, progress tracking, and verification
* Learners building disciplined AI-assisted development habits

## Project Status

This project is under active development. The principles, workflow, templates, and examples will be added incrementally and refined through practical use.

## License

This project is licensed under the [MIT License](LICENSE).
