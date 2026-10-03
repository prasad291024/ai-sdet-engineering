# Architecture

## 1. Purpose

This document describes the architecture and organization of the
`ai-sdet-engineering` repository.

The repository is a progressive AI-SDET engineering apprenticeship.
It combines software testing, automation engineering, API engineering,
AI/ML foundations, LLM engineering, AI evaluation, RAG, agents, AI
security, observability, and an AI-QE capstone.

The repository is designed to evolve incrementally.

Architecture documentation describes both:

- the current repository structure
- the intended progressive structure

Future components must not be represented as implemented components
until they actually exist.

---

## 2. Architectural Principles

The repository follows these principles:

### 2.1 Progressive engineering

Capabilities are developed in stages rather than introduced as isolated
technologies.

The progression is:

SDET
→ Python
→ Automation Architecture
→ API Engineering
→ AI/ML Foundations
→ LLM Engineering
→ LLM Evaluation
→ RAG
→ Agents
→ AI Security
→ Observability
→ AI-QE Capstone

Each stage builds on previously established engineering practices.

### 2.2 Testability first

Systems should be designed so that important behavior can be:

- observed
- validated
- reproduced
- measured
- debugged
- regression-tested

### 2.3 Separation of concerns

Testing, application logic, evaluation logic, data, configuration,
security controls, and reporting should not become unnecessarily coupled.

### 2.4 Deterministic and probabilistic behavior are different

Traditional deterministic assertions and AI semantic evaluation are
treated as related but distinct concerns.

Examples of deterministic checks:

- HTTP status
- schema
- required fields
- data types
- allowed values
- authorization
- tool-call structure

Examples of semantic evaluation:

- correctness
- relevance
- faithfulness
- instruction following
- safety
- groundedness

### 2.5 AI output is not inherently trustworthy

LLM output must be treated as untrusted application output until it has
passed the appropriate validation or evaluation.

### 2.6 Security is part of quality

Security testing is not a separate activity performed only at the end.

AI systems must be evaluated for:

- prompt injection
- jailbreaks
- secret leakage
- unauthorized tool usage
- excessive permissions
- data exfiltration
- unsafe actions
- access-control failures

---

## 3. Current Repository Structure

At the current foundation stage, the repository contains:

```text
ai-sdet-engineering/
│
├── .github/
│   └── workflows/
│       └── ci.yml
│
├── 01-python-sdet-foundation/
│   └── tests/
│       └── test_smoke.py
│
├── docs/
│   ├── GLOSSARY.md
│   ├── ROADMAP.md
│   └── TROUBLESHOOTING.md
│
├── secret_docs/
│   ├── NOTEBOOK.md
│   └── ENGINEERING_JOURNAL.md
│
├── .gitignore
├── README.md
├── ARCHITECTURE.md
├── CHANGELOG.md
├── DECISIONS.md
├── SECURITY.md
├── CONTRIBUTING.md
├── AI-SDET-TRAINING-BLUEPRINT.md
└── CLAUDE.md
```

### Local-only files

`CLAUDE.md` and `secret_docs/` are intentionally excluded from version
control according to the current repository policy.

`secret_docs/` contains personal learning and engineering-history
material that is not intended to form part of the public repository.


## 4. Planned Module Structure

The repository is intended to progressively grow toward:

```text
ai-sdet-engineering/
│
├── 01-python-sdet-foundation/
├── 02-automation-architecture/
├── 03-api-testing/
├── 04-ai-foundations/
├── 05-llm-engineering/
├── 06-llm-evaluation/
├── 07-rag/
├── 08-agents/
├── 09-ai-security/
├── 10-observability/
├── 11-capstone/
│
├── shared/
│
├── docs/
├── .github/
│   └── workflows/
│
├── README.md
├── ARCHITECTURE.md
├── CHANGELOG.md
├── DECISIONS.md
├── SECURITY.md
├── CONTRIBUTING.md
└── AI-SDET-TRAINING-BLUEPRINT.md
```

Directories should be introduced when the corresponding stage begins.
Do not create large numbers of empty future directories merely to make
the tree look complete.

## 5. Module Responsibilities

### 01-python-sdet-foundation

Develop Python capability through SDET-oriented engineering work.

Areas include:

- Python syntax and semantics
- collections
- functions
- modules
- classes
- exceptions
- typing
- JSON
- files
- logging
- configuration
- virtual environments
- dependencies
- pytest
- fixtures
- parametrization
- mocking
- reusable test utilities

### 02-automation-architecture

Develop maintainable automation architecture.

Areas include:

- framework structure
- Page Object Model
- fixtures
- configuration
- test data
- authentication/session reuse
- isolation
- parallel execution
- reporting
- traces
- retries
- flaky-test diagnosis
- maintainability

Existing Playwright experience should be used to deepen architectural
understanding rather than simply repeating UI automation fundamentals.

### 03-api-testing

Develop API engineering and API-quality capability.

Areas include:

- HTTP
- REST
- methods
- status codes
- headers
- authentication
- authorization
- OAuth
- JSON
- schemas
- Pydantic
- pagination
- retries
- timeouts
- rate limits
- idempotency
- contracts
- mocks

Testing should include positive, negative, boundary, malformed,
authentication, authorization, timeout, retry, rate-limit, and contract
scenarios.

### 04-ai-foundations

Build the conceptual model:

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
 ↓
RAG / Agentic Systems

Areas include:

- training
- inference
- datasets
- train/validation/test sets
- overfitting
- generalization
- classification
- precision
- recall
- F1
- neural networks
- optimization
- tokens
- embeddings
- parameters
- context
- attention
- transformers
- sampling
- hallucinations
- model limitations

### 05-llm-engineering

Develop practical LLM application engineering.

Areas include:

- tokenization
- inference
- prompts
- structured outputs
- tool calling
- streaming
- retries
- timeouts
- rate limits
- validation
- error handling
- token usage
- latency
- cost
- configuration
- secrets
- observability

LLM responses must not automatically be treated as trusted values.

### 06-llm-evaluation

Develop AI evaluation as a core SDET discipline.

Evaluation should distinguish:

Deterministic testing
+
Semantic evaluation

Areas include:

- golden datasets
- equivalence testing
- boundary testing
- ambiguity
- multilingual testing
- long-context testing
- metamorphic testing
- adversarial testing
- semantic assertions
- LLM-as-judge
- human evaluation
- calibration
- rubrics
- thresholds
- prompt regression
- model regression

Evaluation should avoid relying on a single composite quality score.

### 07-rag

Develop retrieval-augmented generation systems and their evaluation.

The architectural flow is:

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

Retrieval quality and generation quality should be evaluated
separately.

Important failure modes include:

- missing documents
- stale documents
- duplicate documents
- conflicting documents
- bad parsing
- bad chunking
- irrelevant retrieval
- unsupported claims
- citation failures
- grounding failures
- no-answer failures
- access-control failures
- adversarial documents

### 08-agents

Develop agentic-system engineering.

The progression is:

LLM call
   ↓
Workflow
   ↓
Tool-using application
   ↓
Agentic system

Areas include:

- goals
- state
- tools
- tool schemas
- tool selection
- tool arguments
- observation
- iteration
- planning
- memory
- retries
- recovery
- termination

Testing includes:

- tool selection
- argument validation
- authorization
- tool failures
- unexpected results
- retries
- loops
- termination
- state recovery
- hallucinated tool results
- injection
- unsafe actions
- exfiltration

### 09-ai-security

Treat AI security as AI quality.

Areas include:

- prompt injection
- jailbreaks
- secret leakage
- data exfiltration
- excessive permissions
- authentication
- authorization
- least privilege
- input validation
- output validation
- tool allowlists
- audit logs
- human approval
- data isolation

Important security failures should become regression tests.

### 10-observability

Develop production AI-QE capability.

Areas include:

- logging
- metrics
- traces
- latency
- token usage
- cost
- failure rates
- model behavior
- retrieval behavior
- tool behavior
- evaluation results
- regression detection
- production monitoring

The goal is to make AI-system behavior observable enough to diagnose
quality failures in production.

### 11-capstone

Integrate the complete AI-QE engineering lifecycle:

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

The capstone should demonstrate independent capability across:

- engineering
- testing
- evaluation
- debugging
- security
- observability
- CI/CD
- release quality

## 6. Shared Components

A shared/ area may contain reusable components once multiple modules
demonstrate a genuine need for them.

Examples may include:

- test utilities
- common configuration
- shared fixtures
- evaluation helpers
- data utilities
- reporting utilities

Do not move code into shared/ prematurely.

Duplication should first be understood before introducing shared
abstractions.

## 7. Documentation Architecture

Documentation has separate responsibilities.

### Root documentation

**README.md**
- Public entry point and repository overview.

**ARCHITECTURE.md**
- Repository structure and architectural boundaries.

**CHANGELOG.md**
- Chronological record of repository changes.

**DECISIONS.md**
- Important design and architecture decisions.

**SECURITY.md**
- Security rules and reporting guidance.

**CONTRIBUTING.md**
- Contribution and review workflow.

**AI-SDET-TRAINING-BLUEPRINT.md**
- Curriculum and Definition of Done source of truth.

**docs/**
- Reusable project documentation:
  - GLOSSARY.md
  - ROADMAP.md
  - TROUBLESHOOTING.md

**secret_docs/**
- Private learning and engineering-history material:
  - NOTEBOOK.md
  - ENGINEERING_JOURNAL.md

These files are intentionally excluded from version control.

## 8. CI Architecture

GitHub Actions provides the initial CI layer.

Current workflow:

Git push / Pull Request
          ↓
    GitHub Actions
          ↓
    Python environment
          ↓
       pytest
          ↓
      Pass / Fail

The CI pipeline will evolve as the repository gains:

- formatting checks
- linting
- type checking
- unit tests
- API tests
- evaluation suites
- security tests
- regression tests
- quality gates

CI should remain reproducible and should not depend on developer-specific
machine state.

## 9. Configuration and Secrets

Secrets must never be committed.

Environment-specific configuration should be separated from source
code.

Expected patterns include:

- .env
- .env.example
- environment variables
- CI secrets

.env and other secret-bearing files remain local/ignored.

.env.example may be committed and must contain only:

- variable names
- safe example values
- descriptions where useful

Never put real credentials in .env.example.

## 10. Repository Boundaries

The following boundaries should be maintained:

Application code
       │
       ├── Test code
       │
       ├── Evaluation code
       │
       ├── Test/evaluation data
       │
       ├── Configuration
       │
       └── Observability

These concerns may interact, but should not become unnecessarily
coupled.

AI evaluation should not be hidden inside ordinary functional tests
when the evaluation has materially different semantics or measurement
requirements.

Security controls should not rely solely on prompt instructions.

## 11. Architecture Evolution

Architecture should evolve based on demonstrated engineering needs.

Before introducing a new abstraction, framework, dependency, or top-level
directory, consider:

- What problem does it solve?
- Does the repository already solve the problem?
- Is the abstraction required now?
- What complexity does it introduce?
- How will it be tested?
- How will it be observed?
- How will it affect CI?
- What security implications exist?
- How will future modules use it?
- Is the decision significant enough to record in DECISIONS.md?
