# AI-Assisted Development Playbook

A practical playbook for building readable, testable, maintainable, and reproducible software with AI coding agents.

## Why This Repository Exists

Code is written for computers to execute, but it is also written for people to read, understand, review, and maintain.

AI coding agents can accelerate software development, but generated code is not automatically reliable. Agents may misunderstand requirements, modify code outside the intended scope, overlook project constraints, or claim that work is complete without sufficient verification.

Reliable AI-assisted development still requires:

* Clear requirements
* Explicit authorization and scope boundaries
* Sound design
* Small, verifiable tasks
* Human-readable code
* Independent testing and validation
* Evidence-based completion reports

This repository combines human-centered coding principles with a structured AI-assisted development workflow.

## Core Ideas

### 1. Code Should Be Easy for People to Read

Good code should make its purpose, structure, and main workflow clear without requiring the reader to inspect every implementation detail.

Functions should have clear responsibilities, control flow should remain simple, and names should communicate meaning.

Comments should explain why a decision was made rather than repeat what the code already says.

### 2. Important Information Should Be Stored in Files

Requirements, design decisions, assumptions, task boundaries, and progress should not exist only inside an AI conversation.

Storing important information in project files:

* Keeps AI sessions focused
* Reduces inconsistent assumptions
* Preserves decisions across sessions
* Makes the development process easier to review
* Supports reproducibility
* Reduces dependence on conversational memory

### 3. AI Actions Should Have Explicit Boundaries

A request to explain, review, diagnose, or propose a plan does not automatically authorize code changes.

Before implementation, the agent should understand:

* What outcome is required
* Which files or modules may change
* What is outside the task scope
* Which actions require approval
* How completion will be evaluated

Agents should prefer the smallest change that fully satisfies the requirements.

### 4. AI-Generated Code Must Be Verified

Generating code does not mean that a task is complete.

Important behavior should be tested, quality checks should be run, and results should be compared with explicit acceptance criteria.

An agent should never claim that a test or check passed unless it was actually run successfully.

### 5. Completion Claims Must Be Evidence-Based

A completion report should distinguish between:

* What changed
* What was tested
* What passed or failed
* What was not tested
* What remains uncertain
* What limitations still exist

The agent’s confidence is not a substitute for verification.

## Development Workflow

```text
Requirements → Design → Task Decomposition → Implementation → Verification
```

The workflow has five stages.

### Stage 1 — Requirements

Define:

* Goal
* Inputs
* Outputs
* Constraints
* High-level steps
* Acceptance criteria

The agent should ask questions when ambiguity could materially affect the implementation, scope, output, or an irreversible action.

Minor, safe, and reversible assumptions may be made only when they are stated explicitly.

### Stage 2 — Design

Define:

* Architecture
* Module responsibilities
* Module inputs and outputs
* Interfaces
* Dependencies
* Data flow
* Error-handling strategy
* Testing strategy

Modules should remain as independent and independently testable as practical.

### Stage 3 — Task Decomposition

Break each module into small, independently verifiable tasks.

Each task should identify:

* Goal
* Inputs
* Outputs
* Dependencies
* Files allowed to change
* Acceptance criteria
* Verification commands

### Stage 4 — Implementation

Implementation should follow the confirmed requirements, design, and task boundaries.

The agent should:

* Make the smallest sufficient change
* Avoid unrelated modifications
* Preserve established interfaces unless change is required
* Add or update tests alongside behavioral changes
* Record material assumptions and design changes
* Stop and ask before expanding the agreed scope

### Stage 5 — Verification

Before declaring completion:

* Run relevant automated tests
* Run type, lint, and formatting checks
* Inspect important outputs when appropriate
* Compare the result with the acceptance criteria
* Review edge cases and failure modes
* Confirm that documentation remains accurate
* Confirm that no unrelated files changed
* Report anything that remains unverified

Read the complete workflow in [AI-Assisted Development Workflow](docs/ai-assisted-development-workflow.md).

## Repository Contents

### Current Files

* [AGENTS.md](AGENTS.md): Shared instructions, authorization boundaries, implementation rules, and verification requirements for AI coding agents.
* [Coding Principles](docs/coding-principles.md): Standards for readable, modular, testable, maintainable, and reproducible code.
* [AI-Assisted Development Workflow](docs/ai-assisted-development-workflow.md): The structured development process from requirements definition through verification.
* [LICENSE](LICENSE): MIT License for this repository.

### Current and Planned Structure

```text
ai-assisted-development-playbook/
├── README.md
├── AGENTS.md
├── LICENSE
├── docs/
│   ├── coding-principles.md
│   └── ai-assisted-development-workflow.md
├── templates/                              # Planned
│   ├── requirements.md
│   ├── design.md
│   ├── module-tasks.md
│   ├── progress.md
│   └── decision-log.md
└── examples/                               # Planned
    └── research-project/
```

## How to Use This Playbook

### 1. Read the Core Documents

Start with:

1. [Coding Principles](docs/coding-principles.md)
2. [AI-Assisted Development Workflow](docs/ai-assisted-development-workflow.md)
3. [AGENTS.md](AGENTS.md)

The coding principles define what good code should look like.

The workflow defines how AI-assisted development should proceed.

`AGENTS.md` converts those principles into direct operating instructions for AI coding agents.

### 2. Add the Playbook to a Project

Copy the following files into the project where you want to use the playbook:

```text
AGENTS.md
docs/coding-principles.md
docs/ai-assisted-development-workflow.md
```

When the templates become available, copy the relevant templates as well.

If an AI coding tool does not automatically discover `AGENTS.md`, explicitly instruct it to read the file before beginning work.

### 3. Create Project-Specific Files

For a non-trivial project, maintain:

```text
requirements.md
design.md
progress.md
tasks/
```

These files should contain project-specific information. They should not merely repeat the general rules in this repository.

### 4. Begin With Requirements

Describe the project or task using:

* Goal
* Inputs
* Outputs
* Constraints
* High-level steps
* Acceptance criteria

Do not begin implementation until material ambiguities have been resolved.

### 5. Implement and Verify Incrementally

Work on one bounded task at a time.

After each task:

* Run the relevant checks
* Compare the result with its acceptance criteria
* Update the task checklist
* Update project progress
* Record material decisions or limitations

## Optional Agent Skills

This playbook works without additional Agent Skills. The following third-party Skills can optionally extend the workflow.

### Requirements Interview

The [`grill-me`](https://github.com/mattpocock/skills/tree/main/skills/productivity/grill-me) Skill provides a user-invoked entry point for a structured requirements interview.

It uses the underlying [`grilling`](https://github.com/mattpocock/skills/tree/main/skills/productivity/grilling) Skill to perform the interview process.

Install both:

```bash
npx skills@latest add mattpocock/skills \
  --skill grill-me \
  --skill grilling
```

Invoke Grill Me using the syntax supported by your agent:

```text
/grill-me
$grill-me
Grill me about these requirements before implementation.
```

When Grill Me is active, implementation should not begin until:

* Material ambiguities have been resolved
* Important assumptions have been examined
* Constraints are clear
* Acceptance criteria have been defined
* The user has confirmed the resulting understanding

Confirmed decisions should be recorded in `requirements.md` or `design.md`.

### Skill Discovery

The [`find-skills`](https://github.com/vercel-labs/skills/tree/main/skills/find-skills) Skill helps discover and evaluate Skills for specialized tasks.

Install it with:

```bash
npx skills@latest add vercel-labs/skills --skill find-skills
```

Example requests include:

```text
Find a skill for Python testing.
Is there a skill for reviewing pull requests?
Help me find a skill for data visualization.
```

### Third-Party Skill Notice

These Skills are optional and are not maintained by this repository.

Before installing or updating a third-party Skill:

* Review its source and instructions
* Confirm that it is appropriate for the project
* Check what files or tools it may access
* Avoid assuming that installation commands and behavior will remain unchanged

If an optional Skill is unavailable, the agent should report that limitation rather than pretend that the Skill was activated.

## Quality Gates

For Python projects, the default quality checks are:

```bash
pytest
mypy .
ruff check .
ruff format --check .
```

These commands should be adapted to the project’s actual technology stack.

Test coverage is a diagnostic tool rather than the final objective. Tests should verify meaningful behavior, edge cases, and known failure modes.

A task should not be marked complete merely because a coverage target has been reached.

## Single-Agent and Multi-Agent Work

Use a single agent when:

* The project is small
* Tasks are tightly coupled
* Multiple tasks modify the same files
* Coordination would cost more than it saves

Use multiple agents only when tasks are sufficiently independent.

When using multiple agents:

* The main agent manages requirements, interfaces, integration, and overall progress
* Each sub-agent receives a bounded goal
* Inputs, outputs, allowed files, and acceptance criteria are explicit
* Agents should not modify overlapping files concurrently
* The main agent reviews and verifies the integrated result

Sub-agents can reduce context size, but they do not remove the need for integration review.

## Who This Is For

This playbook is intended for:

* Researchers building data-processing and estimation pipelines
* Developers using Codex, Claude Code, Cursor, or other AI coding agents
* People who want AI-generated code to remain readable and maintainable
* Teams that need explicit requirements and progress tracking
* Learners building disciplined AI-assisted development habits
* Projects where reproducibility and verification matter

## Project Status

This project is being developed incrementally.

* [x] Human-centered coding principles
* [x] AI-assisted development workflow
* [x] Shared agent instructions
* [ ] Requirements and design templates
* [ ] Module-task and progress templates
* [ ] Decision log template
* [ ] Example research project

The documents will continue to be refined through practical use.

## Guiding Principle

AI-assisted development is complete only when:

```text
The requirements are satisfied,
the implementation is understandable,
the relevant checks pass,
and the result has been verified.
```

## License

This project is licensed under the [MIT License](LICENSE).
