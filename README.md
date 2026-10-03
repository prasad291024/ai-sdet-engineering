# AI-SDET Engineering

A hands-on engineering apprenticeship for progressing from experienced SDET automation engineering into AI Quality Engineering.

The repository focuses on building, testing, on the same sentence evaluating, securing, debugging, observing, and operating AI-enabled systems.

This is not intended to teach software testing from the beginning. Existing SDET experience is used as the foundation while progressively building stronger capabilities in Python, engineering architecture, AI/ML, LLMs, evaluation, RAG, agents, AI security, and production quality engineering.

---

## 1. Objective

The target outcome is independent AI-SDET / AI-QE engineering capability.

By the end of the apprenticeship, the learner should be able to:

- Build AI-enabled systems.
- Design maintainable automation and test architecture.
- Test deterministic application behavior.
- Evaluate probabilistic AI behavior.
- Engineer and evaluate RAG systems.
- Test agentic systems and tool usage.
- Identify and test AI-specific security risks.
- Diagnose failures using evidence.
- Build regression protection.
- Integrate quality gates into CI/CD.
- Observe and troubleshoot AI systems in production-like environments.
- Explain engineering and architectural trade-offs.
- Defend testing and quality decisions in technical interviews.

The emphasis is on demonstrated engineering capability rather than syllabus completion.

---

## 2. Learning Approach

The repository follows this engineering loop:

```text
Learn
  ↓
Explain
  ↓
Question
  ↓
Design
  ↓
Implement
  ↓
Test
  ↓
Break
  ↓
Debug
  ↓
Evaluate
  ↓
Refactor
  ↓
Document
  ↓
Commit
  ↓
Push
  ↓
CI
  ↓
Review
  ↓
Improve
```

The central SDET question throughout the apprenticeship is:

> What can fail, how would we detect it, how would we reproduce it,
> how would we measure it, and how would we prevent regression?

For AI systems, this is extended to include:

- Hallucination.
- Semantic correctness.
- Grounding.
- Retrieval failures.
- Tool failures.
- Agent loops.
- Prompt injection.
- Data leakage.
- Unauthorized actions.
- Nondeterminism.
- Cost and latency.
- Observability and production diagnosis.

---

## 3. Curriculum

The detailed curriculum is maintained in:

`AI-SDET-TRAINING-BLUEPRINT.md`

The high-level progression is:

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

See `docs/ROADMAP.md` for the current execution roadmap.

---

## 4. Repository Structure

```text
ai-sdet-engineering/
│
├── AI-SDET-TRAINING-BLUEPRINT.md
│
├── README.md
├── ARCHITECTURE.md
├── CHANGELOG.md
├── DECISIONS.md
├── SECURITY.md
├── CONTRIBUTING.md
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
└── .github/
    └── workflows/
```

Some module directories represent planned curriculum stages and are created progressively as those stages begin.

See `ARCHITECTURE.md` for the detailed repository architecture.

---

## 5. Documentation Map

| Document | Purpose |
|---|---|
| `README.md` | Project overview and entry point |
| `AI-SDET-TRAINING-BLUEPRINT.md` | Detailed curriculum and source of truth |
| `ARCHITECTURE.md` | Repository architecture |
| `CHANGELOG.md` | What changed |
| `DECISIONS.md` | Why important decisions were made |
| `SECURITY.md` | Security requirements and vulnerability handling |
| `CONTRIBUTING.md` | Engineering and contribution workflow |
| `docs/ROADMAP.md` | High-level progression and current status |
| `docs/GLOSSARY.md` | Project terminology |
| `docs/TROUBLESHOOTING.md` | Reusable troubleshooting knowledge |
| `secret_docs/NOTEBOOK.md` | Private learning notes |
| `secret_docs/ENGINEERING_JOURNAL.md` | Private chronological engineering history |

`secret_docs/` is intentionally excluded from version control.

It is a documentation boundary, not a security mechanism.

Secrets, credentials, API keys, passwords, private keys, and other sensitive security material must never be stored there.

---

## 6. Current Repository Status

### Repository Foundation

Status: In progress

Established:

- Git repository and GitHub remote.
- Stable `main` branch.
- Feature-branch workflow.
- Pull-request workflow.
- GitHub Actions CI.
- Initial pytest execution.
- Repository architecture documentation.
- Engineering decision records.
- Security guidance.
- Contribution and review standards.
- Public documentation structure.
- Private engineering-history structure.

The next implementation stage is:

**Python for SDET**

---

## 7. Development Workflow

Normal engineering work follows:

```text
Understand
→ Plan
→ Implement
→ Test
→ Break
→ Debug
→ Document
→ Commit
→ Push
→ CI
→ Pull Request
→ Review
→ Improve
→ Merge
```

Use feature branches for normal development.

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

The `main` branch should remain in a usable state.

See `CONTRIBUTING.md` for the complete workflow.

---

## 8. Testing Philosophy

Traditional deterministic testing remains essential.

Examples include:

- HTTP status codes.
- JSON schemas.
- Required fields.
- Authorization results.
- Database state.
- UI state.
- Contract requirements.

AI systems additionally require evaluation of probabilistic behavior.

Examples include:

- Correctness.
- Relevance.
- Faithfulness.
- Instruction following.
- Safety.
- Grounding.
- Retrieval quality.

Deterministic testing and semantic evaluation are distinct concerns and must not be collapsed into a single testing strategy.

Security is also independent of semantic quality.

For example:

```text
Correct answer + unauthorized data = security failure
Correct answer + secret leakage   = security failure
Useful answer  + unsafe action    = security failure
```

AI outputs, retrieved content, and tool results must be treated as untrusted where applicable.

---

## 9. Security

Security is part of AI quality engineering.

The repository explicitly addresses:

- Secrets management.
- Authentication and authorization.
- Prompt injection.
- Jailbreaks.
- Sensitive-data leakage.
- RAG security.
- Agent and tool security.
- Least privilege.
- Tool allowlists.
- Human approval for high-risk operations.
- CI/CD security.
- Dependency security.
- Security regression testing.

See `SECURITY.md` for the security requirements and reporting process.

---

## 10. Getting Started

### Prerequisites

The repository is progressively built around Python and pytest.

The initial Python test environment should use:

- Python 3.x
- `pytest`

Later stages will introduce additional dependencies as required by the curriculum.

### Run the Tests

From the repository root:

```bash
python -m pytest
```

The exact dependency and environment setup will evolve as implementation modules are introduced.

Do not commit:

- `.venv/`
- `.env`
- API keys.
- Passwords.
- Access tokens.
- Private keys.
- Production credentials.
- Machine-specific files.

---

## 11. Quality Standard

A feature is not complete merely because the happy path works.

Engineering work should consider, where applicable:

- Correctness.
- Negative cases.
- Boundary cases.
- Reliability.
- Regression.
- Performance.
- Security.
- Nondeterminism.
- Recovery.
- Observability.
- Reproducibility.
- Cost.
- Latency.

For AI systems, additionally consider:

- Hallucination.
- Grounding.
- Semantic correctness.
- Retrieval quality.
- Generation quality.
- Tool selection.
- Tool arguments.
- Agent termination.
- Prompt injection.
- Data leakage.
- Unauthorized actions.

See `CONTRIBUTING.md` for the Definition of Done.

---

## 12. Repository Governance

The documentation hierarchy is intentional:

```text
AI-SDET-TRAINING-BLUEPRINT.md
        ↓
Detailed curriculum source of truth

docs/ROADMAP.md
        ↓
High-level execution status

DECISIONS.md
        ↓
Engineering rationale

CHANGELOG.md
        ↓
Change history

secret_docs/ENGINEERING_JOURNAL.md
        ↓
Detailed private engineering history
```

These documents should complement each other rather than become competing sources of truth.

---

## 13. Long-Term Outcome

The final objective is to progress from:

```text
SDET
 ↓
AI-aware SDET
 ↓
AI Test Automation Engineer
 ↓
AI Quality Engineer
 ↓
Independent AI-QE Engineer
```

The final standard is the ability to independently:

```text
Build
  ↓
Test
  ↓
Evaluate
  ↓
Secure
  ↓
Debug
  ↓
Observe
  ↓
Release
  ↓
Monitor
```

AI systems with engineering evidence supporting their quality.
