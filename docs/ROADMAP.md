# AI-SDET Engineering Roadmap

This document provides the high-level execution roadmap for the
AI-SDET Engineering apprenticeship.

The detailed curriculum, stage objectives, projects, milestones, and
Definition of Done are maintained in:

`AI-SDET-TRAINING-BLUEPRINT.md`

This roadmap should remain concise and should not duplicate the detailed
curriculum.

---


## 1. Current State

### Repository Foundation

Status: In progress

Completed:

- Repository established as `ai-sdet-engineering`.
- `main` established as the stable branch.
- Feature-branch and pull-request workflow established.
- Initial GitHub Actions CI established.
- Initial pytest smoke test established.
- Core engineering documentation structure established.
- Public/private documentation boundary established.
- Security engineering expectations established.
- Contribution and review workflow established.

Current documentation foundation:

- `README.md`
- `ARCHITECTURE.md`
- `CHANGELOG.md`
- `DECISIONS.md`
- `SECURITY.md`
- `CONTRIBUTING.md`
- `docs/GLOSSARY.md`
- `docs/ROADMAP.md`
- `docs/TROUBLESHOOTING.md`
- `secret_docs/NOTEBOOK.md`
- `secret_docs/ENGINEERING_JOURNAL.md`

The repository foundation must remain stable before substantial
AI-engineering implementation begins.

---

## 2. Training Progression

The apprenticeship progresses through the following engineering stages:

```text
Repository / Engineering Foundation
                ↓
Python for SDET
                ↓
Automation Architecture
                ↓
API Engineering
                ↓
AI / ML Foundations
                ↓
LLM Engineering
                ↓
LLM Evaluation Engineering
                ↓
RAG Engineering and Evaluation
                ↓
Agent Engineering
                ↓
AI Security
                ↓
Production AI Quality / Observability
                ↓
AI-QE Capstone
                ↓
Continuous Interview Preparation
```

The progression is intentionally cumulative.

Each stage should build capabilities required by later stages rather
than being treated as an isolated course.

---

## 3. Stage Roadmap

### Stage 0 — Repository and Engineering Foundation

Status: In progress

Focus:

* Repository structure.
* Git workflow.
* Branching and pull requests.
* CI.
* Documentation.
* Engineering standards.
* Security baseline.
* Definition of Done.

Exit criteria:

* Repository is reproducible.
* Main branch remains stable.
* CI executes successfully.
* Engineering workflow is understood and followed.
* Documentation accurately describes the repository.
* Changes are traceable through commits, changelog, decisions, and
  private engineering history where appropriate.

---

### Stage 1 — Python for SDET

Status: Next

Focus:

* Python syntax and execution.
* Variables and data types.
* Lists, tuples, sets, and dictionaries.
* Functions.
* Modules and packages.
* Classes and objects.
* Exceptions.
* JSON and file handling.
* Type hints.
* Logging.
* Configuration.
* Virtual environments and dependencies.
* pytest.
* Fixtures.
* Parametrization.
* Mocking.
* API/test utilities.

SDET application:

* Convert familiar testing concepts into Python.
* Build reusable test utilities.
* Design pytest fixtures.
* Create API test helpers.
* Build small automation components.

Exit criteria:

* Can write and explain Python without relying on copy/paste.
* Can structure a small Python test project.
* Can use pytest fixtures and parametrization correctly.
* Can handle failures using appropriate exception mechanisms.
* Can build reusable test utilities.
* Can explain architectural choices.

---

### Stage 2 — Automation Architecture

Status: Planned

Focus:

* Framework architecture.
* Page Object Model.
* Fixtures.
* Configuration.
* Authentication/session reuse.
* Test isolation.
* Test data management.
* Parallel execution.
* Reporting.
* Traces.
* Retries.
* Flaky-test diagnosis.
* Maintainability.

SDET application:

* Rebuild familiar Playwright concepts using explicit architectural
  reasoning.
* Compare TypeScript and Python automation architecture.
* Separate test intent from framework infrastructure.

Exit criteria:

* Can design an automation framework from first principles.
* Can justify POM and fixture boundaries.
* Can identify poor abstractions and unnecessary coupling.
* Can diagnose flaky-test causes rather than simply adding retries.

---

### Stage 3 — API Engineering

Status: Planned

Focus:

* HTTP fundamentals.
* REST.
* Methods and status codes.
* Headers.
* Authentication and authorization.
* OAuth.
* JSON and schemas.
* Pydantic.
* Pagination.
* Timeouts.
* Retries.
* Rate limits.
* Idempotency.
* Contracts.
* Mocking.

Testing:

* Positive cases.
* Negative cases.
* Boundary cases.
* Malformed requests.
* Authentication failures.
* Authorization failures.
* Timeout behavior.
* Retry behavior.
* Rate limiting.
* Contract validation.

Exit criteria:

* Can design API tests beyond happy-path validation.
* Can distinguish authentication from authorization.
* Can reason about retry and idempotency behavior.
* Can validate API contracts.
* Can build reusable API test infrastructure.

---

### Stage 4 — AI / ML Foundations

Status: Planned

Focus:

```text
AI
 ↓
ML
 ↓
Deep Learning
 ↓
Neural Networks
 ↓
Transformers
 ↓
LLMs
 ↓
Generative AI
```

Core concepts:

* Training vs inference.
* Datasets.
* Training/validation/test sets.
* Overfitting.
* Generalization.
* Classification.
* Precision.
* Recall.
* F1.
* Neural networks.
* Optimization.
* Tokens.
* Embeddings.
* Parameters.
* Context.
* Attention.
* Transformers.
* Sampling.
* Hallucinations.
* Model limitations.

SDET perspective:

For each concept:

* What can fail?
* What can be measured?
* What should be tested?
* What evidence demonstrates quality?
* What behavior is deterministic?
* What behavior is probabilistic?

Exit criteria:

* Can explain the core AI/ML concepts without treating LLMs as
  black boxes.
* Can connect model behavior to testing and evaluation concerns.

---

### Stage 5 — LLM Engineering

Status: Planned

Focus:

* Tokenization.
* Inference.
* Prompt design.
* Structured outputs.
* Tool calling.
* Streaming.
* Retries.
* Timeouts.
* Rate limits.
* Model selection.
* Configuration.
* Secrets.
* Token usage.
* Latency.
* Cost.
* Error handling.
* Observability.

Engineering principle:

LLM output is untrusted application input until validated.

Testing:

* Prompt variations.
* Invalid inputs.
* Ambiguous inputs.
* Long context.
* Structured-output failures.
* Timeout behavior.
* Rate limiting.
* Model failures.
* Regression cases.
* Cost and latency boundaries.

Exit criteria:

* Can build an LLM-backed application with appropriate validation,
  error handling, configuration, and observability.
* Can test both application behavior and model-dependent behavior.

---

### Stage 6 — LLM Evaluation Engineering

Status: Planned

Focus:

* Deterministic vs semantic testing.
* Golden datasets.
* Evaluation datasets.
* Rubrics.
* Thresholds.
* Semantic assertions.
* Correctness.
* Relevance.
* Faithfulness.
* Instruction following.
* Safety.
* LLM-as-judge.
* Human evaluation.
* Judge calibration.
* Regression testing.
* Prompt regression.
* Model regression.
* Metamorphic testing.
* Adversarial testing.

Evaluation principle:

Do not reduce AI quality to one composite score.

Exit criteria:

* Can design an evaluation dataset.
* Can define measurable evaluation criteria.
* Can distinguish deterministic failures from semantic failures.
* Can evaluate probabilistic outputs reproducibly.
* Can investigate regressions rather than relying only on pass/fail output.

---

### Stage 7 — RAG Engineering and Evaluation

Status: Planned

Architecture:

```text
Documents
   ↓
Ingestion
   ↓
Parsing
   ↓
Chunking
   ↓
Embeddings / Indexing
   ↓
Retrieval
   ↓
Reranking
   ↓
Context
   ↓
Generation
   ↓
Answer / Evidence
```

Focus:

* Document ingestion.
* Parsing.
* Chunking.
* Embeddings.
* Indexing.
* Retrieval.
* Reranking.
* Context construction.
* Generation.
* Citations.
* Grounding.

Testing:

* Missing documents.
* Stale documents.
* Duplicate documents.
* Conflicting documents.
* Poor chunking.
* Retrieval failures.
* Unsupported claims.
* Citation failures.
* No-answer behavior.
* Access-control failures.
* Adversarial documents.
* Indirect prompt injection.

Quality must be separated into:

1. Retrieval quality.
2. Generation quality.
3. Evidence/citation quality.
4. Security/access-control quality.

Exit criteria:

* Can diagnose whether a RAG failure originates in retrieval,
  context construction, generation, evidence, or security.

---

### Stage 8 — Agent Engineering

Status: Planned

Progression:

```text
LLM Call
   ↓
Workflow
   ↓
Tool-Using Application
   ↓
Agentic System
```

Focus:

* Goals.
* State.
* Tools.
* Tool schemas.
* Tool selection.
* Tool arguments.
* Observation.
* Iteration.
* Planning.
* Memory.
* Loops.
* Termination.
* Retries.
* Recovery.
* Human approval.

Testing:

* Tool selection.
* Tool arguments.
* Authorization.
* Tool failures.
* Unexpected tool results.
* Retry behavior.
* Infinite loops.
* Termination.
* State corruption.
* Recovery.
* Hallucinated tool results.
* Prompt injection.
* Data exfiltration.
* Unsafe actions.

Exit criteria:

* Can explain an agent architecture without reducing agents to
  "LLMs that take actions."
* Can test the agent's control flow, state, tools, authorization,
  recovery, and termination behavior.
* Can identify unsafe autonomy boundaries.

---

### Stage 9 — AI Security

Status: Planned

Focus:

* Prompt injection.
* Jailbreaks.
* Secret leakage.
* Data exfiltration.
* Excessive permissions.
* Authentication.
* Authorization.
* Least privilege.
* Tool allowlists.
* Input validation.
* Output validation.
* Audit logging.
* Human approval.
* Data isolation.
* RAG security.
* Agent/tool security.
* CI/CD security.

Security principle:

Model behavior must never be treated as an authorization mechanism.

Testing:

* Adversarial inputs.
* Malicious documents.
* Unauthorized retrieval.
* Cross-user leakage.
* Cross-tenant leakage.
* Tool abuse.
* Secret extraction.
* Unsafe actions.
* Permission changes.
* Security regression cases.

Exit criteria:

* Can threat-model an AI-enabled system.
* Can design security tests for AI-specific attack surfaces.
* Can convert discovered vulnerabilities into regression tests.
* Can distinguish semantic quality from security acceptance.

---

### Stage 10 — Production AI Quality and Observability

Status: Planned

Focus:

* Logging.
* Metrics.
* Tracing.
* Latency.
* Token usage.
* Cost.
* Error rates.
* Model behavior.
* Retrieval behavior.
* Tool behavior.
* Evaluation monitoring.
* Drift.
* Regression detection.
* Production incident diagnosis.

SDET perspective:

Production quality requires the ability to detect and diagnose failures,
not merely prevent them during development.

Exit criteria:

* Can define useful AI-system quality signals.
* Can investigate production failures using observable evidence.
* Can connect production failures back to reproducible tests and
  evaluation cases.

---

### Stage 11 — AI-QE Capstone

Status: Planned

The capstone integrates the full engineering lifecycle:

```text
Detect
  ↓
Evaluate
  ↓
Diagnose
  ↓
Reproduce
  ↓
Mitigate
  ↓
Regression-test
  ↓
Release-gate
  ↓
Monitor
```

The system should demonstrate:

* AI application engineering.
* Deterministic testing.
* Semantic evaluation.
* RAG and/or agent testing.
* Security testing.
* Observability.
* Failure diagnosis.
* Regression protection.
* CI/CD integration.
* Release-quality decisions.

Exit criteria:

* Can independently build, test, evaluate, secure, debug, observe,
  and explain an AI-enabled system.
* Can demonstrate evidence for quality rather than relying on claims
  that the system "works."

---

## 4. Continuous Interview Preparation

Interview preparation runs throughout the apprenticeship rather than
being deferred until the end.

Areas include:

* Python.
* SDET architecture.
* API testing.
* Automation design.
* CI/CD.
* AI/ML fundamentals.
* LLM engineering.
* Evaluation.
* RAG.
* Agents.
* AI security.
* Debugging.
* System design.
* AI-QE architecture.

Interview exercises should increasingly require:

* Explanation.
* Design.
* Implementation.
* Failure analysis.
* Test strategy.
* Architecture justification.
* Security reasoning.
* Production reasoning.

The objective is independent technical reasoning, not memorization.

---

## 5. Progress Tracking

Progress should be based on demonstrated engineering capability.

A stage is not complete merely because its topics were read.

Evidence of progression may include:

* Working implementation.
* Automated tests.
* Failure cases.
* Debugging evidence.
* Evaluation results.
* Security tests.
* Documentation.
* CI execution.
* Code review.
* Refactoring.
* Technical explanation.
* Interview-style design or debugging exercise.

---

## 6. Roadmap Governance

`AI-SDET-TRAINING-BLUEPRINT.md` is the detailed curriculum source of
truth.

`docs/ROADMAP.md` provides the high-level execution view.

When planned scope changes:

1. Determine whether the change affects the detailed curriculum.
2. Update the blueprint when curriculum scope changes.
3. Update this roadmap when the execution sequence or stage status
   changes.
4. Record meaningful architectural or curriculum decisions in
   `DECISIONS.md`.
5. Record the change in `CHANGELOG.md`.

Do not allow the roadmap and blueprint to become competing sources of
truth.

---

## 7. Definition of Roadmap Completion

The apprenticeship is complete when the learner can independently:

* Build AI-enabled systems.
* Design maintainable test architecture.
* Test deterministic behavior.
* Evaluate probabilistic behavior.
* Test RAG retrieval and generation.
* Test agent control flow and tool usage.
* Identify and test AI-specific security risks.
* Diagnose failures using evidence.
* Build regression protection.
* Integrate quality gates into CI/CD.
* Observe production AI behavior.
* Explain engineering trade-offs.
* Defend architectural and testing decisions in technical interviews.

The final standard is demonstrated engineering capability, not syllabus
completion.
