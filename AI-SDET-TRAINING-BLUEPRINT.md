# AI-SDET Engineering Training Blueprint

## Purpose

This repository is a hands-on apprenticeship for progressing from
experienced SDET/automation engineer to an AI-aware **AI Quality
Engineer / AI-SDET / AI Test Automation Engineer**.

The program is designed around engineering practice rather than passive
learning:

> Learn → Understand → Implement → Test → Break → Debug → Evaluate →
> Commit → Push → Review → Improve

The goal is not merely to learn how to call an LLM API or use an agent
framework. The goal is to understand AI systems well enough to **build,
test, evaluate, secure, automate, debug, and operate them**.

------------------------------------------------------------------------

# 1. Training Outcomes

By the end of the program, the learner should be able to:

### AI foundations

-   Explain AI, ML, deep learning, generative AI, LLMs, RAG, and agents.
-   Explain training vs inference.
-   Understand tokens, embeddings, parameters, context windows,
    temperature, sampling, and model limitations.
-   Understand the basic role of neural networks, attention, and
    transformers.

### AI application engineering

-   Build applications using LLM APIs.
-   Design prompts and structured outputs.
-   Implement retries, timeouts, validation, logging, configuration, and
    error handling.
-   Handle model/provider changes and API failures.
-   Track latency, token usage, and cost.

### AI evaluation

-   Build golden datasets.
-   Separate deterministic checks from probabilistic/model-based
    evaluation.
-   Test correctness, relevance, consistency, safety, refusal behavior,
    and robustness.
-   Use LLM-as-a-judge carefully and calibrate it against human
    evaluation.
-   Perform prompt/model regression testing.

### RAG quality engineering

-   Understand ingestion, chunking, embeddings, retrieval, reranking,
    context construction, and generation.
-   Separate retrieval failures from generation failures.
-   Evaluate retrieval and answer quality independently.
-   Test citations, stale data, conflicting information, missing
    information, access control, and adversarial documents.

### Agent quality engineering

-   Understand the difference between an LLM call, workflow, tool-using
    application, and agentic system.
-   Build a tool-using agent.
-   Test tool selection, argument correctness, state, loops,
    termination, retries, and recovery.
-   Test direct and indirect prompt injection, data exfiltration,
    privilege boundaries, and unsafe tool use.

### Production AI quality engineering

-   Instrument AI applications.
-   Understand traces, logs, metrics, latency, cost, failure rates, and
    quality signals.
-   Establish release gates.
-   Detect regressions.
-   Design rollback/canary strategies.
-   Produce useful incident and evaluation reports.

### SDET career capability

-   Apply conventional SDET principles to AI systems.
-   Explain AI quality engineering decisions in interviews.
-   Demonstrate a portfolio containing real code, tests, datasets,
    evaluations, CI/CD, security testing, and documentation.

------------------------------------------------------------------------

# 2. Training Philosophy

The program follows these principles:

1.  **Engineering over memorization**
2.  **Understanding over copying**
3.  **Building over watching tutorials**
4.  **Testing AI rather than blindly trusting AI**
5.  **Reasoning before framework usage**
6.  **Failure analysis over happy-path demonstrations**
7.  **Deterministic testing where deterministic assertions are
    possible**
8.  **Probabilistic evaluation where AI behavior is inherently
    probabilistic**
9.  **Security and reliability are part of quality**
10. **Every important capability should become reproducible**

We will actively challenge these assumptions:

-   Bigger models are not automatically better.
-   AI does not replace conventional testing.
-   Agents are not automatically better than workflows.
-   LLM output is not automatically trustworthy.
-   AI-generated test cases are not automatically useful.
-   More automation is not automatically better.
-   A high evaluation score does not automatically mean production
    readiness.

------------------------------------------------------------------------

# 3. Program Structure

## Nominal duration

**32 weeks (\~8 months)** at approximately **6--8 hours/week**.

The duration is adaptive.

A topic may be shortened when competence is demonstrated and extended
when the learner cannot independently explain or implement it.

The objective is **mastery, not completion of a calendar**.

------------------------------------------------------------------------

# 4. Stage Map

  ------------------------------------------------------------------------------------
  Stage                            Weeks Primary Focus            Major Output
  ---------------- --------------------- ------------------------ --------------------
  0                                 0--1 Engineering/repository   Working learning
                                         setup                    repo + CI

  1                                 1--2 Python for SDET          Tested Python
                                                                  foundation

  2                                 3--5 Automation architecture  Maintainable test
                                                                  framework

  3                                 6--8 API engineering          API test/contract
                                                                  suite

  4                                9--11 AI/ML foundations        AI mental-model
                                                                  notes + experiments

  5                               12--14 LLM engineering          LLM
                                                                  application/client

  6                               15--18 LLM evaluation           Evaluation framework

  7                               19--22 RAG engineering +        Evidence-grounded
                                         evaluation               RAG system

  8                               23--26 Agents + security        Tool-using agent +
                                                                  security suite

  9                               27--30 Production AI-QE         Observability + CI
                                                                  quality gates

  10                              31--32 Capstone + interviews    Portfolio-grade
                                                                  AI-QE platform
  ------------------------------------------------------------------------------------

Stages may overlap when useful.

------------------------------------------------------------------------

# 5. Repository Strategy

We will maintain **one primary learning repository** rather than
creating a new repository for every lesson.

Proposed repository:

``` text
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
│   ├── fixtures/
│   ├── utilities/
│   ├── datasets/
│   └── config/
│
├── docs/
├── reports/
│
├── .github/
│   └── workflows/
│
├── README.md
└── AI-SDET-TRAINING-BLUEPRINT.md
```

This is a **progressive engineering repository**, not a single giant
application.

Projects will be cumulative where practical.

For example:

``` text
LLM application
      ↓
LLM evaluation
      ↓
RAG
      ↓
Agent
      ↓
Security testing
      ↓
Observability
      ↓
CI/CD quality gates
      ↓
Final AI-QE platform
```

At the end, a polished capstone may optionally be extracted into a
separate portfolio repository.

------------------------------------------------------------------------

# 6. Engineering Workflow

Every substantial implementation follows:

``` text
Understand requirement
        ↓
Design
        ↓
Implement
        ↓
Write tests
        ↓
Run locally
        ↓
Introduce/encounter failure
        ↓
Debug
        ↓
Improve
        ↓
Commit
        ↓
Push
        ↓
CI
        ↓
Review
        ↓
Refactor
```

We will not push every tiny experiment.

The Git history should eventually demonstrate meaningful engineering
progression.

------------------------------------------------------------------------

# 7. Stage 0 --- Repository and Engineering Baseline

## Objectives

-   Establish Git/GitHub workflow.
-   Establish Python environment.
-   Establish pytest.
-   Establish CI.
-   Establish coding/documentation conventions.
-   Understand how the training repository will evolve.

## Activities

-   Create repository.
-   Configure `.gitignore`.
-   Create Python virtual environment.
-   Install project dependencies.
-   Create initial pytest suite.
-   Configure GitHub Actions.
-   Create README.
-   Create basic project structure.
-   Make first meaningful commit.
-   Push and verify CI.

## Definition of Done

-   Repository exists.
-   Tests run locally.
-   CI runs automatically.
-   README explains the repository.
-   Learner understands every file created.

------------------------------------------------------------------------

# 8. Stage 1 --- Python for SDET

## Topics

-   Variables and data types
-   Lists, tuples, sets, dictionaries
-   Conditions and loops
-   Functions
-   Modules and packages
-   Exceptions
-   Classes and objects
-   Type hints
-   File handling
-   JSON
-   Environment variables
-   Logging
-   Virtual environments
-   Dependency management
-   pytest
-   Fixtures
-   Parametrization
-   Assertions
-   Mocking
-   Temporary directories/files

## SDET application

Build small utilities such as:

-   Test-data generator
-   JSON validator
-   API response helper
-   Configuration loader
-   Retry utility
-   Test-report parser

## Definition of Done

The learner can write and test small Python modules without copying a
tutorial solution.

------------------------------------------------------------------------

# 9. Stage 2 --- Automation Architecture

This stage strengthens formal framework-design knowledge while
leveraging existing Playwright experience.

## Topics

-   Test architecture
-   Page Object Model
-   Fixtures
-   Test isolation
-   Configuration
-   Environment management
-   Authentication/session reuse
-   Test data management
-   Parallel execution
-   Worker distribution
-   Reporting
-   Screenshots/traces
-   Retry strategy
-   Flaky-test diagnosis
-   Dependency management
-   Maintainability
-   Separation of concerns

## Engineering exercise

Design a framework from requirements rather than modifying an existing
framework.

The learner must explain:

-   Why the folders exist.
-   Why a fixture exists.
-   Why a page object exists.
-   How authentication is handled.
-   How test data is isolated.
-   How parallel execution works.
-   What happens when a test fails.

## Definition of Done

The learner can design a maintainable automation framework and justify
its architecture.

------------------------------------------------------------------------

# 10. Stage 3 --- API Engineering

## Topics

-   HTTP fundamentals
-   REST
-   Methods
-   Status codes
-   Headers
-   Authentication
-   OAuth concepts
-   JSON
-   JSON Schema
-   Pydantic
-   Pagination
-   Timeouts
-   Retries
-   Rate limiting
-   Idempotency
-   Contract testing
-   Mocking

## Project

### API Test / Contract Test Kit

The suite should include:

-   Positive tests
-   Negative tests
-   Malformed requests
-   Empty input
-   Boundary cases
-   Authentication failures
-   Authorization failures
-   Timeout behavior
-   Retry behavior
-   Rate-limit behavior
-   Schema validation
-   Contract validation

## Definition of Done

A reproducible API test suite runs locally and in CI and produces
understandable failure classifications.

------------------------------------------------------------------------

# 11. Stage 4 --- AI and ML Foundations

This stage prevents framework-first AI learning.

## Concepts

### AI

-   AI scope
-   Rule-based systems
-   Machine learning
-   Generative AI

### Machine Learning

-   Training
-   Inference
-   Features
-   Labels
-   Models
-   Supervised learning
-   Unsupervised learning
-   Classification
-   Regression
-   Clustering

### Dataset concepts

-   Training set
-   Validation set
-   Test set
-   Data leakage
-   Overfitting
-   Underfitting
-   Generalization

### Evaluation

-   Accuracy
-   Precision
-   Recall
-   F1
-   Confusion matrix
-   ROC-AUC
-   False positives
-   False negatives

### Neural networks

-   Neurons
-   Layers
-   Activation functions
-   Loss
-   Optimization
-   Gradient descent
-   Backpropagation

### Transformer foundations

-   Sequence modeling
-   Attention
-   Self-attention
-   Tokens
-   Embeddings
-   Positional information
-   Transformer architecture

## SDET connection

For every concept ask:

> How would an SDET test this?

Examples:

-   Dataset quality
-   Data leakage
-   Boundary conditions
-   Model generalization
-   False positives/negatives
-   Reproducibility
-   Regression
-   Distribution changes

## Definition of Done

The learner can explain how modern LLMs fit into the broader AI/ML
landscape without treating LLMs as magic.

------------------------------------------------------------------------

# 12. Stage 5 --- LLM Engineering

## Topics

-   Tokenization
-   Context windows
-   Parameters
-   Model weights
-   Inference
-   Next-token prediction
-   Sampling
-   Temperature
-   Top-k
-   Top-p
-   Prompt structure
-   System/developer/user instructions
-   Structured outputs
-   Tool calling
-   Streaming
-   Errors
-   Retries
-   Rate limits
-   Cost
-   Latency
-   Model selection
-   Provider abstraction
-   Secrets management

## Project

### LLM Application / Client

Build a small application that:

-   Sends structured requests to an LLM.
-   Validates responses.
-   Handles failures.
-   Logs useful metadata.
-   Tracks latency.
-   Tracks token/cost information where available.
-   Uses configuration rather than hard-coded secrets.
-   Has automated tests.

## Definition of Done

The learner can build an LLM-backed application as an engineer rather
than merely calling an API from a script.

------------------------------------------------------------------------

# 13. Stage 6 --- LLM Evaluation Engineering

This is one of the most important stages for AI-SDET.

## Why

Traditional assertion:

``` text
actual == expected
```

LLM testing often involves:

``` text
Is this response correct?
Is it relevant?
Is it grounded?
Is it safe?
Does it follow the instruction?
```

These questions may not have one exact string answer.

## Topics

-   Golden datasets
-   Test-case design
-   Equivalence classes
-   Boundary cases
-   Ambiguous prompts
-   Multilingual inputs
-   Long-context inputs
-   Adversarial inputs
-   Metamorphic testing
-   Deterministic assertions
-   Semantic assertions
-   LLM-as-a-judge
-   Human evaluation
-   Judge calibration
-   Rubrics
-   Thresholds
-   Regression testing
-   Prompt versioning
-   Model versioning

## Project

### Prompt Regression Laboratory

The system should:

-   Run a versioned dataset.
-   Run multiple prompts/models where appropriate.
-   Perform deterministic checks.
-   Perform model-based evaluation.
-   Produce category-level results.
-   Capture failed evidence.
-   Compare versions.
-   Detect regressions.
-   Run in CI.

## Required metadata

At minimum:

``` text
application version
prompt version
model/provider
dataset version
evaluator version
latency
token usage/cost where available
evaluation results
failed evidence
```

## Definition of Done

Every model-graded result has a documented rubric, threshold, evaluator
version, and a manually reviewed sample.

------------------------------------------------------------------------

# 14. Stage 7 --- RAG Engineering and Quality

## Architecture

``` text
Documents
   ↓
Ingestion
   ↓
Parsing
   ↓
Chunking
   ↓
Embeddings
   ↓
Vector/index storage
   ↓
Retrieval
   ↓
Optional reranking
   ↓
Context construction
   ↓
LLM
   ↓
Answer + evidence
```

## Topics

-   Embeddings
-   Similarity
-   Chunking
-   Metadata
-   Vector search
-   Filters
-   Retrieval
-   Reranking
-   Context windows
-   Grounding
-   Citations
-   Faithfulness
-   Answer relevance
-   Context precision
-   Context recall

## RAG failure modes

-   Missing documents
-   Poor chunking
-   Duplicate content
-   Stale documents
-   Conflicting documents
-   Wrong retrieval
-   Missing citations
-   Unsupported claims
-   Unauthorized retrieval
-   Adversarial documents

## Project

### Evidence-Grounded Knowledge Assistant

Build and evaluate a RAG system over legally usable public
documentation.

Create a verified dataset containing questions and, where possible:

-   expected answer
-   relevant document
-   section/page
-   supporting evidence
-   expected no-answer cases

## Definition of Done

Retrieval quality and generation quality are measured separately, and
failures can be localized to retrieval or generation.

------------------------------------------------------------------------

# 15. Stage 8 --- Agents

Agents are a major part of the program.

## First establish the distinctions

We will compare:

``` text
LLM call
   ↓
Workflow
   ↓
Tool-using LLM application
   ↓
Agentic system
```

The exact boundary is contextual and will be studied rather than reduced
to a buzzword.

## Core concepts

-   Goals
-   State
-   Tools
-   Tool schemas
-   Tool selection
-   Tool arguments
-   Observation
-   Iteration
-   Planning
-   Memory
-   Loops
-   Termination
-   Recovery
-   Human approval

## Project

### Test Failure Investigation Agent

Example workflow:

``` text
Failed test
   ↓
Agent
   ├── Retrieve test details
   ├── Read logs
   ├── Inspect screenshots/trace
   ├── Search recent failures
   ├── Inspect relevant code/config
   ├── Form hypothesis
   └── Produce investigation report
```

## Agent testing

Test:

-   Tool selection
-   Tool argument correctness
-   Invalid tool arguments
-   Tool failures
-   Missing data
-   Unexpected tool output
-   Loops
-   Termination
-   Retry behavior
-   State corruption
-   Hallucinated tool results
-   Unauthorized actions
-   Reproducibility

## Definition of Done

The learner can explain, build, test, and debug a tool-using agent
without relying on framework abstractions as a black box.

------------------------------------------------------------------------

# 16. Stage 9 --- AI Security

Security is integrated into agent/RAG testing rather than treated as an
afterthought.

## Topics

-   Direct prompt injection
-   Indirect prompt injection
-   Jailbreaks
-   Obfuscation
-   Data exfiltration
-   Secret leakage
-   Prompt exposure
-   Cross-user/tenant data access
-   Tool abuse
-   Excessive permissions
-   Input validation
-   Output sanitization
-   Allowlists
-   Least privilege
-   Authentication/authorization
-   Rate limiting
-   Audit logging
-   Human approval

## Security testing

Build attack datasets and automated tests.

Examples:

``` text
Malicious document
        ↓
RAG retrieval
        ↓
Can it manipulate the model?
```

and:

``` text
Malicious user input
        ↓
Agent
        ↓
Can it invoke an unauthorized tool?
```

## Definition of Done

Security failures are reproducible, classified, reported, and
incorporated into regression testing.

------------------------------------------------------------------------

# 17. Stage 10 --- Production AI Quality Engineering

## Observability

Understand:

-   Logs
-   Metrics
-   Traces
-   Correlation IDs
-   Tool-call traces
-   Retrieval traces
-   Evaluation traces

## Operational metrics

Track where relevant:

-   Latency
-   Error rate
-   Token usage
-   Cost
-   Throughput
-   Tool failure rate
-   Retrieval failure rate
-   Evaluation score
-   Regression rate

## Production controls

-   Quality gates
-   Risk thresholds
-   Canary releases
-   Rollback
-   Prompt versioning
-   Model versioning
-   Dataset versioning
-   Evaluator versioning
-   Drift detection
-   Incident analysis

## Definition of Done

A change can be evaluated before release and its quality/operational
impact can be observed after release.

------------------------------------------------------------------------

# 18. Final Capstone

## AI Quality Engineering Platform

The final system should integrate the major capabilities developed
throughout the program.

Conceptually:

``` text
                    ┌────────────────────┐
                    │   AI Application   │
                    └─────────┬──────────┘
                              │
              ┌───────────────┼────────────────┐
              ↓               ↓                ↓
           LLM/RAG          Agent           Tools
              │               │                │
              └───────────────┼────────────────┘
                              ↓
                    ┌──────────────────┐
                    │  AI-QE Platform  │
                    └──────────────────┘
                              │
       ┌──────────────┬───────┼────────┬──────────────┐
       ↓              ↓       ↓        ↓              ↓
   Functional      Eval    Security  Observability   CI/CD
     Tests
```

The platform should demonstrate:

1.  Test generation where useful.
2.  API testing.
3.  LLM evaluation.
4.  Prompt regression.
5.  RAG evaluation.
6.  Agent/tool testing.
7.  Security testing.
8.  Deterministic checks.
9.  Model-based evaluation.
10. Reporting.
11. CI/CD gates.
12. Observability.
13. Failure localization.
14. Reproduction.
15. Regression prevention.

The flagship workflow should demonstrate:

> **Detect → Evaluate → Diagnose → Reproduce → Mitigate →
> Regression-test → Release-gate → Monitor**

------------------------------------------------------------------------

# 19. Release Scorecard

We will avoid reducing AI quality to one misleading composite number.

Instead, maintain separate dimensions such as:

### Quality

-   Correctness
-   Relevance
-   Faithfulness
-   Context precision
-   Context recall

### Safety

-   Refusal behavior
-   Prompt injection resistance
-   Data leakage
-   Unauthorized actions

### Agent reliability

-   Tool selection
-   Argument correctness
-   Termination
-   Recovery

### Operations

-   Latency
-   Cost
-   Error rate
-   Throughput

A release decision should depend on **business/risk thresholds**, not a
single arbitrary AI score.

------------------------------------------------------------------------

# 20. Git and CI/CD Expectations

Throughout the program we will practice:

-   Meaningful commits
-   Branches
-   Pull-request style changes
-   Code review thinking
-   CI
-   Test reports
-   Failure artifacts
-   Environment configuration
-   Secrets handling
-   Reproducible commands

Typical workflow:

``` bash
git checkout -b feature/<name>

# implement
# test
# debug

git status
git diff
git add .
git commit -m "Add <meaningful change>"
git push
```

The exact branching strategy can evolve as the repository matures.

------------------------------------------------------------------------

# 21. Documentation Expectations

Important projects must contain:

-   README
-   Architecture explanation
-   Setup instructions
-   Test commands
-   Example usage
-   Design decisions
-   Known limitations
-   Failure modes
-   Evaluation methodology
-   CI behavior

Important experiments should be documented in Markdown.

The repository should eventually tell the story of the engineering
journey.

------------------------------------------------------------------------

# 22. Learning and Evaluation Loop

For each major topic:

``` text
1. Learn
2. Explain back
3. Question
4. Implement
5. Test
6. Break
7. Debug
8. Refactor
9. Document
10. Commit
11. Push
12. Review
```

I will periodically evaluate:

-   Conceptual understanding
-   Implementation quality
-   Testing depth
-   Debugging ability
-   Architecture reasoning
-   AI understanding
-   Security thinking
-   Production thinking
-   Interview readiness

When an answer is weak, it will be classified explicitly as:

-   Correct
-   Mostly correct
-   Partially correct
-   Incorrect
-   Missing an important dimension

------------------------------------------------------------------------

# 23. Interview Preparation

Interview preparation is continuous, not postponed until the final week.

We will practice:

### Conceptual

-   Explain transformers.
-   Explain embeddings.
-   Explain RAG.
-   Explain hallucinations.
-   Explain agents.

### Coding

-   Python
-   APIs
-   Data processing
-   Test utilities

### SDET

-   Framework design
-   Parallelism
-   Test isolation
-   Flaky tests
-   CI/CD
-   API testing

### AI-QE

-   LLM evaluation
-   Golden datasets
-   LLM judges
-   RAG evaluation
-   Agent testing
-   Prompt injection
-   AI observability

### System design

-   Design an AI testing platform.
-   Design an LLM evaluation pipeline.
-   Design a RAG quality system.
-   Design an agent testing architecture.

The goal is to eventually explain **why** a design is appropriate, not
merely name tools.

------------------------------------------------------------------------

# 24. Definition of Program Completion

The program is not complete because all folders exist.

It is complete when the learner can independently:

-   Explain the AI/ML/LLM landscape.
-   Build an LLM application.
-   Design meaningful AI test cases.
-   Build an evaluation dataset.
-   Implement deterministic and probabilistic evaluation.
-   Diagnose RAG failures.
-   Test agents and tools.
-   Perform AI security testing.
-   Instrument an AI application.
-   Integrate AI quality checks into CI/CD.
-   Analyze failures and recommend mitigations.
-   Explain architectural tradeoffs.
-   Defend design decisions in an interview.
-   Demonstrate a portfolio-quality AI-QE project.

------------------------------------------------------------------------

# 25. First Practical Milestone

We will **not** immediately create all folders.

Our first milestone is:

``` text
Create repository
      ↓
Create Python environment
      ↓
Install pytest
      ↓
Create first test
      ↓
Run test
      ↓
Configure CI
      ↓
Run CI
      ↓
Create README
      ↓
Commit
      ↓
Push
```

Then the repository becomes the permanent home for the training.

------------------------------------------------------------------------

# 26. Guiding Principle

The final objective is not:

> "I know AI."

It is:

> **"I can engineer quality into AI systems."**

That means understanding the system deeply enough to ask:

-   What can fail?
-   Why can it fail?
-   How can I detect the failure?
-   How can I reproduce it?
-   How can I measure it?
-   How can I prevent regression?
-   What are the security implications?
-   What happens in production?
-   What evidence supports the release decision?

That is the mindset this program is designed to develop.
