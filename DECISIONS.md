# Engineering Decisions

This document records important decisions that shape the architecture, workflow, governance, testing strategy, and long-term structure of the AI-SDET apprenticeship.

This file focuses on why decisions were made. It does not serve as a chronological list of repository changes. Implementation history belongs in `secret_docs/ENGINEERING_JOURNAL.md`, while repository changes belong in `CHANGELOG.md`.

---

## Decision 001 — One Repository for the Entire AI-SDET Apprenticeship

### Decision

Use a single repository as the primary home for the complete AI-SDET apprenticeship.

### Rationale

The apprenticeship is intended to represent one continuous engineering journey rather than a collection of unrelated projects.

A single repository provides:

- One source for the complete learning history.
- Consistent engineering standards across modules.
- Shared tooling and automation infrastructure.
- Centralized CI/CD validation.
- A unified documentation structure.
- Traceability between curriculum, implementation, testing, and engineering decisions.
- A realistic repository structure similar to an enterprise engineering project.

This also allows the project to demonstrate progression from foundational testing concepts to advanced SDET, automation, AI-assisted testing, and engineering practices.

### Consequence

Modules should remain logically separated within the repository while sharing common project infrastructure where appropriate.

---

## Decision 002 — Progressive Module Structure

### Decision

Organize the apprenticeship as a progressive sequence of modules rather than treating all topics as independent exercises.

### Rationale

The objective is to demonstrate measurable progression in engineering capability.

Each module should build on concepts, tools, practices, or artifacts introduced earlier.

The progression should support:

- Increasing technical complexity.
- Increasing automation maturity.
- Progressive introduction of engineering practices.
- Reuse of established project infrastructure.
- Traceability between learning objectives and implementation work.
- Demonstration of practical SDET capabilities rather than isolated coding exercises.

### Consequence

New modules should fit into the existing progression instead of introducing unrelated structures or duplicating infrastructure unnecessarily.

---

## Decision 003 — Git Feature-Branch / Pull-Request Workflow

### Decision

Use a Git feature-branch and pull-request workflow for repository changes.

### Rationale

The apprenticeship should follow professional software-engineering practices rather than relying exclusively on direct commits to the main branch.

The workflow provides experience with:

- Isolated feature development.
- Small, reviewable changes.
- Pull requests.
- Code and test review.
- CI validation before merging.
- Traceable implementation history.
- Controlled changes to the main branch.

This also makes the repository history more representative of an enterprise engineering workflow.

### Consequence

Changes should normally be developed on a dedicated branch and integrated through a pull request after the required validation passes.

---

## Decision 004 — GitHub Actions CI

### Decision

Use GitHub Actions as the repository CI platform.

### Rationale

GitHub Actions provides native integration with the repository and supports automated validation without requiring separate CI infrastructure for the apprenticeship.

It can provide a consistent execution path for:

- Automated tests.
- Linting and static checks.
- Build or validation tasks.
- Future module-specific quality gates.

Using CI from the beginning also ensures that automated validation is treated as part of the engineering workflow rather than as an activity performed only after development is complete.

### Consequence

Repository changes should be designed so that appropriate automated validation can run through GitHub Actions.

---

## Decision 005 — Public `docs/` vs Private `secret_docs/`

### Decision

Separate documentation into a public `docs/` area and a private `secret_docs/` area.

### Rationale

Not all project documentation has the same publication requirements.

`docs/` is intended for documentation that is safe to publish and share with the repository.

`secret_docs/` is intended for private learning material, internal engineering history, and other documentation that is intentionally excluded from the public repository.

The separation provides an explicit documentation boundary between:

- Public project documentation.
- Private learning material.
- Internal engineering history.
- Other documentation that should not be publicly published.

The separation is a repository-governance control. It should not be treated as the only security mechanism.

Security secrets, credentials, tokens, API keys, passwords, private keys, or other sensitive security material must never be stored in `secret_docs/`.

### Consequence

Contributors must determine whether documentation is public or private before committing it.

Private documentation should remain under `secret_docs/` and must be excluded from the public repository through the appropriate repository configuration.

Security secrets must be handled through appropriate secret-management mechanisms and must not be committed to the repository.

---

## Decision 006 — `AI-SDET-TRAINING-BLUEPRINT.md` as Curriculum Source of Truth

### Decision

Use `AI-SDET-TRAINING-BLUEPRINT.md` as the authoritative curriculum definition for the apprenticeship.

### Rationale

The apprenticeship contains multiple modules, exercises, technical areas, and progression stages.

A single curriculum source of truth prevents the learning plan from becoming fragmented across multiple documents.

The blueprint should define:

- Curriculum structure.
- Module sequence.
- Learning objectives.
- Required capabilities.
- Expected progression.
- Module relationships.
- Completion criteria where applicable.

Other documentation may explain implementation details or engineering decisions, but it should not silently redefine the curriculum.

### Consequence

Changes to the apprenticeship curriculum should be reflected in `AI-SDET-TRAINING-BLUEPRINT.md`.

Other documents should reference the blueprint rather than becoming competing curriculum sources.

---

## Decision 007 — Deterministic Testing and Semantic AI Evaluation Are Distinct Concerns

### Decision

Treat deterministic software testing and semantic AI evaluation as separate testing concerns.

### Rationale

Traditional automated tests generally depend on deterministic or explicitly defined expected behavior.

Examples include:

- HTTP status codes.
- Database values.
- Schema validation.
- Exact field presence.
- Contract validation.
- UI state.
- Authentication behavior.
- Functional workflow outcomes.

AI systems introduce another class of validation where the output may be variable while still satisfying the intended requirement.

Examples include:

- Natural-language responses.
- Generated test cases.
- Classification results.
- Summaries.
- Reasoning-dependent outputs.
- LLM-generated artifacts.

An exact string comparison is often unsuitable for these cases.

The project therefore separates:

```
Deterministic Testing
    ↓
Is the observable system behavior within the defined contract?

Semantic AI Evaluation
    ↓
Does the AI output satisfy the intended meaning, quality,
or behavioral criteria?
```

The two concerns may be used together in the same test scenario, but they should remain conceptually and architecturally distinguishable.

A test may first validate deterministic structure or contract requirements and then perform semantic evaluation of the content.

### Consequence

Test design should explicitly identify whether an assertion is:

- Deterministic.
- Semantic.
- Security-related.
- Performance-related.
- Or a combination of these concerns.

AI evaluation should use appropriate datasets, rubrics, thresholds, and evaluation methods rather than relying exclusively on exact string matching.

---

## Decision 008 — Separate Change History, Decision Records, and Engineering Journal

### Decision

Maintain three separate historical records:

- `CHANGELOG.md` for what changed.
- `DECISIONS.md` for why significant decisions were made.
- `secret_docs/ENGINEERING_JOURNAL.md` for detailed chronological engineering history.

### Rationale

These records answer different questions and therefore should not be merged into a single document.

```
CHANGELOG
    ↓
What changed?

DECISIONS
    ↓
Why was an important decision made?

ENGINEERING_JOURNAL
    ↓
How did the engineering work actually happen?
```

Keeping these concerns separate allows:

- The changelog to remain concise.
- The decision record to remain focused on rationale.
- The engineering journal to preserve detailed implementation history.
- Public documentation to remain focused and readable.
- Private engineering history to remain separate from public project documentation.

This structure prevents duplication while maintaining traceability across the project's lifecycle.

### Consequence

Repository changes should update `CHANGELOG.md`.

Meaningful architectural, engineering, workflow, testing, security, or governance choices should be recorded in `DECISIONS.md`.

Detailed implementation history, debugging sessions, commands, failures, corrections, experiments, and lessons learned should be recorded in `secret_docs/ENGINEERING_JOURNAL.md`.

The three documents should complement one another rather than duplicate the same information.
