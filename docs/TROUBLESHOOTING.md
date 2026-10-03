# Troubleshooting

This document records reusable troubleshooting knowledge for the
AI-SDET Engineering repository.

The purpose is to help engineers diagnose recurring problems without
repeating the original investigation from scratch.

Detailed chronological engineering history belongs in:

`secret_docs/ENGINEERING_JOURNAL.md`

---

## 1. Troubleshooting Principles

When something fails:

1. **Reproduce the failure.**
2. **Capture the exact error and relevant evidence.**
3. **Identify the smallest failing component.**
4. **Determine the root cause.**
5. **Apply the smallest appropriate fix.**
6. **Re-run the failing test or workflow.**
7. **Run the appropriate regression scope.**
8. **Document the reusable lesson when applicable.**

**Do not hide failures by:**

- Removing or weakening assertions.
- Adding unnecessary retries.
- Ignoring CI failures.
- Changing expected results without understanding the cause.
- Treating flaky behavior as normal.
- Suppressing useful error information.

The objective is to understand the failure, not merely make the failure
disappear.

---

## 2. Local Test Failures

### Symptom

A pytest test fails locally.

### Investigation

Check:

- **The complete pytest output.**
- **The failing test and assertion.**
- **Test input and expected result.**
- **Fixtures used by the test.**
- **Configuration and environment variables.**
- **Whether the failure is reproducible.**
- **Whether another test modifies shared state.**

### Common Causes

- **Incorrect assertion.**
- **Incorrect test data.**
- **Fixture configuration problem.**
- **Application defect.**
- **Environment difference.**
- **Dependency behavior.**
- **Shared-state contamination.**

### Prevention

- **Keep tests isolated.**
- **Use explicit fixtures.**
- **Avoid unnecessary shared mutable state.**
- **Preserve useful failure evidence.**
- **Add regression coverage for confirmed defects.**

---

## 3. Pytest Reports No Tests Collected

### Symptom

Pytest exits without executing tests and reports that no tests were
collected.

### Cause

No test files or test functions match pytest's discovery rules, or the
configured test path does not contain tests.

### Investigation

Check:

- **Test file naming.**
- **Test function naming.**
- **Test directory.**
- **Pytest configuration.**
- **CI working directory.**

### Resolution

Add or correctly name the intended test and verify discovery locally.

For example:

```text
tests/
└── test_smoke.py
```

with a test function such as:

```python
def test_example():
    assert True
```

### CI Consideration

A CI workflow that runs pytest should not silently convert a
zero-test condition into success unless that behavior is explicitly
required and justified.

A repository expected to contain tests should treat unexpected
zero-test collection as a signal requiring investigation.

---

## 4. CI Passes Locally but Fails in GitHub Actions

### Symptom

A test or workflow passes locally but fails in CI.

### Investigation

Compare:

- **Python version.**
- **Dependency versions.**
- **Operating system.**
- **Environment variables.**
- **Working directory.**
- **File paths.**
- **Installed packages.**
- **Available credentials.**
- **Network assumptions.**
- **Test ordering.**
- **Parallel execution behavior.**

### Common Causes

- **Environment differences.**
- **Missing dependency.**
- **Missing configuration.**
- **Platform-specific behavior.**
- **Incorrect relative path.**
- **Timezone assumptions.**
- **Test isolation problems.**
- **Dependency version differences.**

### Prevention

- **Pin or appropriately constrain important dependencies.**
- **Keep CI configuration explicit.**
- **Avoid machine-specific paths.**
- **Avoid relying on undeclared environment state.**
- **Reproduce CI failures locally when practical.**

---

## 5. CI Workflow Fails Because of Missing Tests

### Symptom

A CI workflow running pytest fails because pytest returns a
non-zero exit status when no tests are collected.

### Diagnosis

The test runner is functioning, but the repository does not yet contain
a test matching the configured discovery rules.

### Resolution

Add the intended initial test or correct the test-discovery configuration.

Do not weaken the CI command merely to make the workflow green.

### Prevention

Establish at least one meaningful smoke test before requiring automated
test execution as a repository quality gate.

---

## 6. Flaky Test

### Symptom

The same test sometimes passes and sometimes fails without an
intentional code change.

### Investigation

Determine whether the nondeterminism originates from:

- **The test.**
- **The application.**
- **The environment.**
- **A dependency.**
- **Timing.**
- **Concurrency.**
- **External services.**
- **Shared state.**
- **Randomness.**

Run the test repeatedly when appropriate and capture enough evidence
to identify the source of nondeterminism.

### Common Causes

- **Race conditions.**
- **Uncontrolled test data.**
- **Shared state.**
- **Timing assumptions.**
- **External dependencies.**
- **Improper cleanup.**
- **Parallel execution.**
- **Random input without controlled seeds.**

### Resolution

Correct the underlying source of nondeterminism.

Retries may be appropriate for genuinely transient conditions, but they
must not be used to conceal deterministic failures.

---

## 7. Environment or Configuration Problem

### Symptom

Tests or application code behave differently because required
configuration is missing or incorrect.

### Investigation

Check:

- **Required environment variables.**
- **Configuration files.**
- **Active virtual environment.**
- **Dependency installation.**
- **Runtime version.**
- **`.env` handling.**
- **CI environment configuration.**

### Security Rule

Never resolve configuration problems by committing real credentials,
tokens, passwords, private keys, or production secrets.

Use environment variables or an appropriate secret-management mechanism.

`.env.example` may document variable names with dummy values.

---

## 8. Authentication Failure

### Symptom

A test or API request unexpectedly returns an authentication failure.

### Investigation

Check:

- Whether credentials are present.
- Whether credentials are expired.
- Authentication method.
- Token format.
- Request headers.
- Authentication endpoint.
- Environment configuration.
- Clock/time validity where relevant.

### Important Distinction

**Authentication answers:**

> Who are you?

**Authorization answers:**

> What are you allowed to do?

Do not diagnose an authorization failure as an authentication problem
without evidence.

---

## 9. Authorization Failure

### Symptom

A validly authenticated request is rejected because the requested
operation or resource is not permitted.

### Investigation

Check:

- **User identity.**
- **Roles.**
- **Permissions.**
- **Resource ownership.**
- **Tenant boundaries.**
- **Policy configuration.**
- **Authorization decision.**
- **Resource-level access controls.**

### AI-System Consideration

An LLM's decision to request a tool or retrieve information must never
be treated as authorization.

Authorization must be independently enforced by the application.

---

## 10. API Test Failure

### Symptom

An API test receives an unexpected response.

### Investigation

Check:

- **HTTP method.**
- **URL.**
- **Query parameters.**
- **Request headers.**
- **Authentication.**
- **Request body.**
- **Response status.**
- **Response headers.**
- **Response body.**
- **Schema.**
- **Server-side logs where available.**

### Test Design

Separate:

- **Transport behavior.**
- **HTTP contract.**
- **Authentication.**
- **Authorization.**
- **Business behavior.**
- **Error handling.**

A successful HTTP response does not automatically mean the API
behavior is correct.

---

## 11. Timeout

### Symptom

A test or API request exceeds its configured timeout.

### Investigation

Determine whether the timeout originates from:

- **The test.**
- **Client configuration.**
- **Application processing.**
- **Network.**
- **External dependency.**
- **Database.**
- **Rate limiting.**
- **Resource exhaustion.**

### Do Not

Do not immediately increase the timeout without identifying why the
operation is slow.

A larger timeout may hide a performance or reliability problem.

---

## 12. LLM Output Fails an Exact Assertion

### Symptom

An LLM test fails because the generated text does not exactly match the
expected string.

### Investigation

Determine whether the requirement is:

- **Exact and deterministic.**
- **Structurally constrained.**
- **Semantically constrained.**
- **Probabilistic.**

### Resolution

If the requirement is semantic, use an evaluation method appropriate to
the behavior instead of requiring brittle exact-string equality.

If the requirement is genuinely deterministic, preserve the
deterministic assertion.

### Principle

Do not replace a valid deterministic requirement with a weak semantic
check merely because the deterministic test is inconvenient.

Do not impose brittle exact-string matching when the requirement
explicitly permits valid variation.

---

## 13. LLM Quality Regression

### Symptom

The system still produces valid-looking responses, but quality has
degraded after a prompt, model, configuration, or retrieval change.

### Investigation

Compare:

- **Previous evaluation results.**
- **Current evaluation results.**
- **Evaluation dataset.**
- **Prompt version.**
- **Model/version.**
- **Model parameters.**
- **Retrieved context.**
- **Evaluation criteria.**
- **Failure categories.**

### Resolution

Reproduce the failing evaluation cases and determine whether the
regression originates in:

- **Prompt changes.**
- **Model changes.**
- **Context changes.**
- **Retrieval changes.**
- **Application logic.**
- **Evaluation methodology.**

Preserve important regression cases in the evaluation dataset.

---

## 14. RAG Retrieval Failure

### Symptom

The generated answer is incorrect because relevant information was not
retrieved.

### Investigation

Inspect the RAG pipeline:

```text
Document
→ Parsing
→ Chunking
→ Embedding / Indexing
→ Retrieval
→ Reranking
→ Context
→ Generation
```

Determine the first stage where the expected information is lost.

### Common Causes

- **Poor document parsing.**
- **Incorrect chunking.**
- **Poor embeddings.**
- **Retrieval threshold.**
- **Incorrect metadata filtering.**
- **Missing indexing.**
- **Query mismatch.**
- **Reranking failure.**

### Principle

Do not diagnose every RAG failure as an LLM-generation problem.

Separate retrieval quality from generation quality.

---

## 15. RAG Answer Is Unsupported

### Symptom

The system produces an answer that is not supported by the retrieved
evidence.

### Investigation

Check:

- **Retrieved documents.**
- **Retrieved chunks.**
- **Context supplied to the model.**
- **Generated claim.**
- **Citation/evidence mapping.**

Determine whether the failure is caused by:

- **Retrieval.**
- **Context construction.**
- **Generation.**
- **Citation handling.**

### Security Consideration

Retrieved content and metadata are untrusted inputs.

Citations or metadata must not be treated as authorization controls.

---

## 16. Prompt Injection

### Symptom

Untrusted input changes model behavior in an unintended way.

### Investigation

Identify:

- **Source of the untrusted content.**
- **Instructions supplied by the application.**
- **Model-visible context.**
- **Tools available to the model.**
- **Data available to the system.**
- **Resulting model behavior.**

For RAG systems, inspect whether retrieved documents contain
instruction-like content.

### Prevention

Use:

- **Input validation where appropriate.**
- **Clear trust boundaries.**
- **Untrusted-content isolation.**
- **Tool allowlists.**
- **Independent authorization.**
- **Output validation.**
- **Least privilege.**
- **Human approval for high-risk operations where required.**

Do not assume prompt wording alone provides a security boundary.

---

## 17. Agent Uses the Wrong Tool

### Symptom

An agent selects an inappropriate tool or supplies incorrect arguments.

### Investigation

Capture:

- **Agent goal.**
- **Available tools.**
- **Tool descriptions.**
- **Selected tool.**
- **Tool arguments.**
- **Validation result.**
- **Authorization result.**
- **Tool response.**
- **Subsequent agent behavior.**

### Testing

Test:

- **Correct tool selection.**
- **Incorrect tool selection.**
- **Missing arguments.**
- **Invalid arguments.**
- **Boundary arguments.**
- **Unauthorized tool requests.**
- **Malicious tool results.**

### Security Principle

Model tool selection is not authorization.

The application must independently validate and authorize every
security-sensitive tool invocation.

---

## 18. Agent Loop Does Not Terminate

### Symptom

An agent repeatedly calls tools or continues reasoning without reaching
a valid termination condition.

### Investigation

Check:

- Termination criteria.
- Maximum iterations.
- State transitions.
- Tool results.
- Error recovery.
- Planning logic.

### Prevention

Define explicit:

- Termination conditions.
- Iteration limits.
- Failure states.
- Recovery behavior.
- Human-approval boundaries where applicable.

An agent should fail safely rather than continue indefinitely.

---

## 19. Secret Appears in Logs or Artifacts

### Symptom

A credential, token, or sensitive value appears in logs, reports,
screenshots, traces, or CI artifacts.

### Immediate Response

Treat the value as exposed.

Do not simply delete the visible log entry and assume the problem is
resolved.

Determine:

- Where the secret originated.
- Where it was recorded.
- Which systems may have retained it.
- Whether rotation or revocation is required.

### Prevention

- Never log secrets.
- Avoid including credentials in test artifacts.
- Review traces and screenshots.
- Minimize CI environment exposure.
- Use appropriate secret-management mechanisms.

Follow `SECURITY.md` for security incident handling.

---

## 20. Dependency Problem

### Symptom

A test or application begins failing after a dependency installation or
upgrade.

### Investigation

Check:

- Dependency version.
- Transitive dependencies.
- Lock/configuration files.
- Release notes where available.
- Reproducibility in a clean environment.
- Whether the failure existed before the upgrade.

### Prevention

Use deliberate dependency management.

Before introducing a dependency, consider:

- Maintenance status.
- Security vulnerabilities.
- License implications.
- Transitive dependencies.
- Long-term repository impact.

---

## 21. When to Add a Troubleshooting Entry

Add an entry when:

- The failure is likely to recur.
- The diagnosis required non-obvious investigation.
- The problem has a reusable solution.
- The issue exposes an important engineering principle.
- Future contributors would benefit from the documented investigation
  pattern.

Do not add every transient error.

The goal is reusable engineering knowledge.

---

## 22. Relationship to Other Documentation

Use the documentation system consistently:

| Document | Purpose |
|---|---|
| `README.md` | What the project is and how to start |
| `ARCHITECTURE.md` | How the repository is structured |
| `CHANGELOG.md` | What changed |
| `DECISIONS.md` | Why important decisions were made |
| `SECURITY.md` | Security requirements and handling |
| `CONTRIBUTING.md` | How engineering work is performed |
| `docs/GLOSSARY.md` | Project terminology |
| `docs/TROUBLESHOOTING.md` | Reusable problem-solving knowledge |
| `docs/ROADMAP.md` | Planned progression |
| `secret_docs/ENGINEERING_JOURNAL.md` | Detailed private engineering history |

Avoid duplicating detailed investigation history here.

Record reusable conclusions here and retain the chronological investigation in the engineering journal.
