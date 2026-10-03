# Contributing

## 1. Purpose

This document defines how engineering work should be performed in this repository.

This is an engineering-learning repository for the AI-SDET apprenticeship. Contributions should strengthen the existing architecture, preserve traceability, and demonstrate disciplined software-engineering practices.

Contributors should not treat the repository as a collection of isolated exercises.

Each contribution should fit the existing:

- Curriculum structure.
- Repository architecture.
- Testing strategy.
- Security model.
- Documentation model.
- CI workflow.
- Engineering history.

The objective is to produce changes that are understandable, testable, reviewable, secure, and maintainable.

---

## 2. Engineering Workflow

Engineering work follows this lifecycle:

```text
Understand
   ↓
Plan
   ↓
Implement
   ↓
Test
   ↓
Break
   ↓
Debug
   ↓
Document
   ↓
Commit
   ↓
Push
   ↓
CI
   ↓
Pull Request
   ↓
Review
   ↓
Improve
   ↓
Merge
```

### Understand

Before changing the repository:

- Understand the requirement or learning objective.
- Inspect the relevant existing implementation.
- Check the repository structure.
- Check related documentation.
- Check existing tests.
- Check `AI-SDET-TRAINING-BLUEPRINT.md` when the work affects curriculum scope.
- Check `DECISIONS.md` when the work may conflict with an existing architectural decision.
- Check `SECURITY.md` when the change introduces security-sensitive behavior.
- Avoid creating a new implementation when an existing component already provides the required capability.

### Plan

Before implementation:

- Define the intended outcome.
- Identify the files and components likely to change.
- Identify dependencies and integration points.
- Identify the tests required to prove the change.
- Identify documentation that must be updated.
- Identify security implications.
- Identify whether the change introduces a meaningful architectural decision.

For larger changes, establish the plan before writing implementation code.

### Implement

Implementation should:

- Follow the existing project structure.
- Follow established naming conventions.
- Prefer existing reusable components over duplicate implementations.
- Keep changes focused on the intended task.
- Avoid unrelated refactoring.
- Preserve existing functionality unless the change explicitly requires modification.
- Keep configuration separate from implementation where appropriate.

### Test

Test the expected behavior before considering the implementation complete.

Testing should include:

- Existing tests affected by the change.
- New tests for new behavior.
- Regression tests for fixed defects where appropriate.
- Negative-path testing where relevant.
- Security testing for security-sensitive behavior.
- AI-specific evaluation where AI behavior is involved.

### Break

Do not stop after confirming the happy path.

Actively test failure conditions and boundary cases.

Examples include:

- Invalid input.
- Missing data.
- Unexpected state.
- Incorrect configuration.
- Authorization failures.
- Dependency failures.
- Network failures.
- Malformed responses.
- AI-generated unexpected output.
- Tool misuse.
- Prompt-injection attempts where applicable.

The objective is to understand how the implementation behaves when assumptions fail.

### Debug

When a test or workflow fails:

1. Reproduce the failure.
2. Capture the relevant evidence.
3. Isolate the failing component.
4. Determine the root cause.
5. Fix the underlying problem.
6. Re-run the relevant test.
7. Run the appropriate regression scope.
8. Document important findings.

Do not hide failures by weakening assertions, adding unnecessary retries, or changing expected results without understanding the cause.

### Document

Update documentation when the change affects:

- Architecture.
- Setup or execution.
- Security.
- Configuration.
- Project terminology.
- Troubleshooting.
- Engineering decisions.
- Curriculum structure.
- Future contributors.

Use the appropriate document rather than placing all information in one file.

### Commit

Create a focused commit after the task is complete.

The commit should contain the implementation and the public documentation/history updates belonging to that logical change.

Private engineering history may be recorded separately in `secret_docs/ENGINEERING_JOURNAL.md` and is intentionally not committed.

### Push and CI

Push the feature branch and allow CI to validate the change.

Do not treat local success as a substitute for CI validation.

Investigate CI failures rather than bypassing or weakening quality gates.

### Pull Request

Open a pull request when the branch is ready for review.

The pull request should explain:

- What changed.
- Why it changed.
- How it was tested.
- Relevant security considerations.
- Relevant documentation changes.
- Known limitations or follow-up work.

### Review and Improve

Address review feedback with focused changes.

Re-run the relevant validation after making changes.

Keep the pull request history understandable.

### Merge

Merge only after the required review and CI checks have passed.

The main branch should remain in a usable state.

---

## 3. Branching Strategy

Use short-lived feature branches for engineering work.

Recommended naming format:

```text
feature/<short-description>
fix/<short-description>
test/<short-description>
docs/<short-description>
refactor/<short-description>
security/<short-description>
ci/<short-description>
experiment/<short-description>
```

Examples:

```text
feature/add-api-smoke-tests
fix/auth-fixture-timeout
test/add-negative-rag-cases
docs/update-contributing-guide
security/harden-tool-authorization
ci/add-security-scan
experiment/compare-rag-chunking
```

### Branching Rules

- Branch from the current main branch.
- Keep branches focused on one logical change.
- Use lowercase names with hyphens.
- Avoid personal names, ticketless vague names, and temporary names such as `test`, `changes`, or `new`.
- Do not develop directly on the main branch for normal feature work.
- Delete merged branches when they are no longer required.

### Experiment Branches

Experiment branches are intended for exploratory work, especially AI-related experiments.

Examples include:

- Comparing embedding models.
- Testing LLM parameters.
- Comparing RAG chunking strategies.
- Evaluating LLM judges.
- Exploring alternative evaluation methods.

An experiment does not automatically become repository architecture.

Before adopting an experiment into the main implementation:

- Evaluate the results.
- Document relevant findings.
- Identify trade-offs.
- Record a decision when the experiment results in a meaningful architectural choice.

---

## 4. Implementation Expectations

Contributors are expected to understand the existing implementation before extending it.

### Architecture

New modules and features must:

- Fit the existing repository structure.
- Reuse established utilities and fixtures where applicable.
- Avoid parallel implementations of the same capability.
- Preserve clear separation between modules.
- Avoid introducing dependencies without a clear need.
- Follow existing configuration and environment conventions.
- Avoid coupling unrelated modules.

If a proposed change requires a structural exception, document the rationale and record a decision when appropriate.

### Curriculum Alignment

New learning modules should align with `AI-SDET-TRAINING-BLUEPRINT.md`.

Do not introduce substantial curriculum content that exists outside the established progression without first updating the curriculum source of truth.

### Code Quality

Implementation should be:

- Readable.
- Testable.
- Maintainable.
- Consistent with the existing codebase.
- Free of unnecessary duplication.
- Free of dead code.
- Explicit about important failure conditions.

Do not add abstractions solely because they appear architecturally sophisticated.

Use the simplest structure that satisfies the requirement and preserves the project's long-term architecture.

---

## 5. Testing Expectations

Tests are part of the implementation, not an optional follow-up activity.

### Minimum Expectations

A contribution should include appropriate tests for the behavior it changes.

Depending on the change, this may include:

- Unit tests.
- Integration tests.
- API tests.
- UI tests.
- End-to-end tests.
- Regression tests.
- Security tests.
- AI evaluation tests.

### Deterministic Testing

Use deterministic assertions when the expected behavior is deterministic.

Examples:

- HTTP status.
- Schema.
- Required fields.
- Database state.
- Authorization result.
- UI state.
- Contract requirements.

Avoid weakening deterministic assertions merely because a test is inconvenient to maintain.

### Failure Testing

Where applicable, test:

- Invalid inputs.
- Boundary conditions.
- Error responses.
- Permission failures.
- Dependency failures.
- Unexpected states.
- Recovery behavior.

### Regression Testing

A confirmed defect should receive a regression test when practical.

Important security failures must be preserved as regression tests.

### Flaky Tests

Do not normalize flaky tests as acceptable behavior.

When a test is flaky:

1. Reproduce it.
2. Determine the source of nondeterminism.
3. Identify whether the problem is in the test, application, environment, or dependency.
4. Correct the root cause.
5. Verify stability through repeated execution where appropriate.
6. Document the issue when it provides a reusable engineering lesson.

Retries must not be used to conceal deterministic failures.

---

## 6. AI Evaluation Expectations

AI-enabled functionality requires evaluation beyond traditional deterministic assertions.

### Separate Deterministic and Semantic Validation

A test should identify whether it is validating:

- Deterministic behavior.
- Semantic behavior.
- Security behavior.
- Performance behavior.
- Or a combination.

Semantic AI evaluation should not be reduced to brittle exact-string assertions when the requirement permits valid output variation.

### Semantic Evaluation

Where appropriate, use:

- Representative datasets.
- Evaluation rubrics.
- Explicit criteria.
- Thresholds.
- Expected behavioral properties.
- Regression datasets.
- Appropriate evaluation methods.

The evaluation method should match the behavior being tested.

### Security Is Independent of Quality

A semantically correct response can still be a security failure.

Examples:

```text
Correct answer + unauthorized data = security failure
Correct answer + secret leakage   = security failure
Useful answer  + unsafe action    = security failure
```

AI evaluation must therefore not treat a high semantic-quality result as evidence that security requirements have been satisfied.

### LLM and Agent Testing

For AI systems, consider applicable risks such as:

- Prompt injection.
- Jailbreak attempts.
- Sensitive-data leakage.
- Unauthorized information retrieval.
- Unsafe tool usage.
- Incorrect tool arguments.
- Unauthorized actions.
- Malicious retrieved content.
- Cross-user or cross-tenant data exposure.

AI outputs and tool results must be treated as untrusted where applicable.

### Evaluation Reproducibility

AI evaluations should record enough information to understand:

- What was evaluated.
- Which dataset or inputs were used.
- What criteria were applied.
- What threshold or acceptance rule was used.
- What failed.
- Whether the failure represents a regression.

Do not claim deterministic behavior from a probabilistic system without appropriate evidence.

---

## 7. Security Expectations

Security is part of normal engineering work.

Contributors must follow `SECURITY.md` and apply security considerations throughout planning, implementation, testing, and review.

### Secrets

Never commit:

- API keys.
- Passwords.
- Access tokens.
- Credentials.
- Private keys.
- Production secrets.
- Real sensitive environment values.

Use environment variables and appropriate secret-management mechanisms.

`.env.example` may document required variable names, but must contain dummy values only.

### AI Security

Treat LLM outputs as untrusted until validated.

For applicable systems:

- Validate AI-generated outputs before critical use.
- Defend against prompt injection.
- Consider jailbreak resistance.
- Prevent secret leakage.
- Validate tool calls and results.
- Use tool allowlists.
- Apply authorization independently of model decisions.
- Use human approval for high-risk actions where required.
- Isolate untrusted documents and tool results.

### RAG Security

For RAG implementations:

- Treat retrieved content and metadata as untrusted.
- Consider malicious or poisoned documents.
- Test indirect prompt injection.
- Enforce document-level access control.
- Prevent cross-user or cross-tenant data leakage.
- Validate retrieved content.
- Isolate untrusted content before passing it to an LLM or downstream tool.
- Do not treat citations or metadata as proof of authorization.

### CI/CD Security

Contributors must consider security implications of CI execution.

Do not:

- Expose secrets in CI logs.
- Include secrets in test reports.
- Include credentials in traces, screenshots, or generated artifacts.
- Give untrusted pull requests unnecessary privileged credentials.
- Grant CI workflows more permissions than required.

Security scanning and automated testing must not introduce a new path for secret disclosure.

### Dependencies

New dependencies should have a clear justification.

Contributors should consider:

- Maintenance status.
- Known vulnerabilities.
- License requirements where applicable.
- Transitive dependencies.
- CI/security scanning impact.

---

## 8. Documentation Expectations

Documentation is part of the implementation.

Update documentation when a change affects how another engineer would understand, run, test, secure, or extend the repository.

### Documentation Responsibilities

Use each document for its intended purpose:

| Document | Purpose |
|---|---|
| `README.md` | What the project is, setup, and basic usage |
| `ARCHITECTURE.md` | Repository structure and major component relationships |
| `CHANGELOG.md` | What changed |
| `DECISIONS.md` | Why important decisions were made |
| `SECURITY.md` | Security requirements and vulnerability handling |
| `CONTRIBUTING.md` | How contributors should work |
| `secret_docs/NOTEBOOK.md` | Personal learning notes, gotchas, open questions, and ideas |
| `docs/TROUBLESHOOTING.md` | Solved problems, symptoms, causes, and fixes |
| `docs/GLOSSARY.md` | Project-specific terminology |
| `docs/ROADMAP.md` | Planned work and scope |
| `secret_docs/ENGINEERING_JOURNAL.md` | Detailed private engineering history |

Do not duplicate the same information across documents unless each occurrence serves a distinct purpose.

### Changelog

Every completed change should have a `CHANGELOG.md` entry.

Use the established format:

```markdown
## YYYY-MM-DD
- Added / Changed / Fixed / Removed: short description
- Why: reason for the change
- Touched: list of files changed
```

### Decisions

When a meaningful architectural, structural, testing, security, workflow, or technology decision is made, update `DECISIONS.md`.

### Engineering Journal

Detailed implementation history belongs in:

```text
secret_docs/ENGINEERING_JOURNAL.md
```

Use it for appropriate details such as:

- Debugging history.
- Important failures.
- Experiments.
- Commands and investigation steps.
- Corrections.
- Lessons learned.
- Implementation reasoning.

The three historical records remain distinct:

```text
CHANGELOG
    ↓
What changed?

DECISIONS
    ↓
Why was an important decision made?

ENGINEERING_JOURNAL
    ↓
How did the engineering work happen?
```

---

## 9. Commit Standards

Commits should represent completed, logical engineering changes.

### Commit Format

Use a concise type and description:

```text
<type>: <short description>
```

Recommended types:

```text
feat
fix
test
docs
refactor
security
ci
chore
```

Examples:

```text
feat: add API smoke test
test: add negative authentication coverage
fix: correct transaction status assertion
security: isolate untrusted RAG content
docs: document module contribution workflow
ci: add pytest workflow
```

### Commit Rules

- Use clear and specific messages.
- Keep one logical change per commit.
- Include related tests and documentation in the same commit when they belong to the change.
- Do not commit known broken work to the main branch.
- Do not use meaningless messages such as `update`, `changes`, `fix`, or `final`.
- Do not commit secrets or sensitive local configuration.

---

## 10. Pull Requests

Every non-trivial change should be integrated through a pull request.

### A Pull Request Should Explain

- What changed.
- Why the change was required.
- What was tested.
- CI status.
- Security considerations.
- Documentation changes.
- Known limitations.
- Follow-up work, if any.

### Pull Request Expectations

Before requesting review:

- The branch is focused on one logical objective.
- Relevant tests pass locally.
- CI has been allowed to run.
- Relevant failures have been investigated.
- Documentation is updated.
- `CHANGELOG.md` is updated.
- `DECISIONS.md` is updated when required.
- Security implications have been considered.
- No secrets or sensitive artifacts are included.

Do not use a pull request to bundle unrelated cleanup with a feature unless the cleanup is required for the change.

---

## 11. Code Review

Code review is part of the engineering process.

Reviewers should evaluate:

### Correctness

- Does the implementation satisfy the requirement?
- Are important edge cases covered?
- Are failure conditions handled correctly?

### Test Quality

- Does the test prove the intended behavior?
- Are assertions meaningful?
- Are deterministic and semantic evaluations appropriately separated?
- Are regression cases included where appropriate?

### Architecture

- Does the change fit the existing structure?
- Does it introduce unnecessary duplication?
- Does it create inappropriate coupling?
- Does it respect established decisions?

### Security

- Could the change expose secrets or sensitive information?
- Are authorization boundaries preserved?
- Are AI outputs treated as untrusted where applicable?
- Are tool calls independently authorized?
- Are RAG access controls preserved?
- Could CI execution expose credentials or sensitive artifacts?

### Documentation

- Can another contributor understand the change?
- Were affected documents updated?
- Are new project-specific terms documented?
- Was a meaningful architectural decision recorded?

### Review Feedback

Authors should:

- Respond to review comments.
- Make the requested corrections where appropriate.
- Explain disagreements with technical reasoning.
- Re-run relevant tests after changes.
- Keep the pull request focused.

Reviewers should focus on the implementation rather than the contributor.

---

## 12. Definition of Done

A contribution is complete when all applicable requirements below are satisfied.

### Understanding and Planning

- [ ] Requirement or learning objective is understood.
- [ ] Existing implementation was inspected before adding new functionality.
- [ ] Relevant architecture and governance documents were checked.
- [ ] Curriculum alignment was verified when applicable.

### Implementation

- [ ] Change follows the existing repository structure.
- [ ] Naming conventions are followed.
- [ ] Existing reusable components were considered.
- [ ] No unnecessary duplication was introduced.
- [ ] No unrelated changes were included.

### Testing

- [ ] Appropriate automated tests were added or updated.
- [ ] Existing affected tests pass.
- [ ] Negative and boundary cases were considered.
- [ ] Regression coverage was added for important defects where appropriate.
- [ ] Flaky behavior was investigated rather than hidden.
- [ ] AI evaluation was added when AI behavior requires semantic validation.

### AI Quality and Security

- [ ] Deterministic and semantic assertions are appropriately distinguished.
- [ ] AI outputs are validated where they affect critical behavior.
- [ ] Applicable prompt-injection and jailbreak risks were considered.
- [ ] Tool authorization is independent of model tool selection.
- [ ] RAG access-control risks were considered where applicable.
- [ ] Security failures cannot be overridden by a semantic-quality score.

### Security

- [ ] No secrets or credentials were committed.
- [ ] Sensitive data is not present in logs or generated artifacts.
- [ ] Authentication and authorization requirements were considered.
- [ ] Least privilege is applied where applicable.
- [ ] Relevant dependency and security risks were considered.
- [ ] CI/CD security implications were reviewed.
- [ ] Relevant security tests were added or updated.

### Documentation

- [ ] Affected documentation was updated.
- [ ] `CHANGELOG.md` was updated.
- [ ] `DECISIONS.md` was updated when a meaningful decision was made.
- [ ] `docs/TROUBLESHOOTING.md` was updated when a problem was solved and the knowledge is reusable.
- [ ] `docs/GLOSSARY.md` was updated when a new project-specific term was introduced.
- [ ] `secret_docs/ENGINEERING_JOURNAL.md` was updated when detailed engineering history is useful for the apprenticeship.

### Git and Review

- [ ] Commit messages clearly describe the changes.
- [ ] Changes are contained in the appropriate feature branch.
- [ ] CI has completed successfully or any failure has been explicitly investigated.
- [ ] Pull request description explains the change and validation.
- [ ] Review feedback has been addressed.
- [ ] The main branch remains in a usable state after merge.

A contribution is not considered complete merely because the code works locally.

The contribution is complete when the implementation, tests, security, documentation, history, CI validation, and review requirements applicable to the change have been satisfied.
