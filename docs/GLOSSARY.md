# Glossary of Technical Terms

This document contains shared technical terminology used throughout the AI-SDET Engineering apprenticeship and repository.

---


## A

**Agent** - An AI-enabled system that can use tools, observe results, maintain state, and iteratively execute actions toward a goal.

Agent behavior should be distinguished from a simple LLM call or a fixed workflow.

**AI Evaluation** - The systematic measurement of AI-system behavior against defined criteria, datasets, rubrics, thresholds, or other evaluation methods.

AI evaluation may include semantic quality, correctness, relevance, faithfulness, instruction following, safety, and other properties.

**AI-QE** - AI Quality Engineering: the engineering discipline concerned with building, testing, evaluating, securing, observing, and maintaining the quality of AI-enabled systems.

**API (Application Programming Interface)** - A set of rules and protocols for building and interacting with software applications, allowing different systems to communicate with each other.

**Assertion** - A statement in testing that verifies a specific condition is true; if false, the test fails.

**Automation Architecture** - The structural design of automated testing systems, including frameworks, patterns, and reusable components.

## B

**Baseline** - A fixed reference point used for comparison in testing, monitoring, or performance evaluation.

**Black Box Testing** - Testing methodology that examines system functionality without knowledge of internal code structure or implementation.

**Boundary Testing** - Testing approach that focuses on values at the edges of input domains, including minimum, maximum, and just-beyond boundaries.

**Build** - The process of compiling source code into executable software or preparing artifacts for deployment.

## C

**CI/CD (Continuous Integration/Continuous Deployment)** - Practices that automate the integration, testing, and deployment of code changes.

**CAPTCHA** - Completely Automated Public Turing test to tell Computers and Humans Apart; a security mechanism to distinguish human users from bots.

**Chaos Engineering** - The discipline of experimenting on a system to build confidence in its capability to withstand turbulent conditions in production.

**Checksum** - A value calculated from data to detect errors that may have been introduced during transmission or storage.

**Containerization** - The practice of packaging software with its dependencies and configuration into isolated, portable units (containers).

**Contract Testing** - Testing approach that verifies interactions between services meet predefined agreements or contracts.

## D

**Data Drift** - Changes in the distribution of input data over time that can affect model performance.

**Deterministic** - Producing the same output given the same input every time; predictable and reproducible.

**DevOps** - A set of practices that combines software development (Dev) and IT operations (Ops) to shorten the development lifecycle.

**Domain Specific Language (DSL)** - A computer language specialized to a particular application domain.

## E

**End-to-End (E2E) Testing** - Testing methodology that validates complete user workflows from start to finish.

**Environment** - The collection of external conditions, configuration, and resources in which software runs.

**Equivalence Partitioning** - A black box testing technique that divides input data into partitions of equivalent data from which test cases can be derived.

**Error Budget** - The maximum amount of time a service can be unavailable or degraded while still meeting its service level objective (SLO).

## F

**False Negative** - A test result that incorrectly indicates a condition is absent when it is actually present.

**False Positive** - A test result that incorrectly indicates a condition is present when it is actually absent.

**Feature Flag** - A technique that allows developers to enable or disable functionality remotely without deploying new code.

**Flaky Test** - A test that exhibits both passing and failing results with the same code, often due to timing or environmental factors.

**Fuzz Testing** - An automated software testing technique that provides invalid, unexpected, or random data as inputs to a program.

## G

**Golden Dataset** - A carefully curated set of input/output pairs used as a benchmark for testing and evaluation.

**Governance** - The framework of rules, practices, and processes by which an organization is directed and controlled.

**Gradle** - An open-source build automation system focused on flexibility and performance.

**Gray Box Testing** - Testing methodology that combines knowledge of internal workings with external testing techniques.

## H

**Hallucination** - In AI, the generation of information that is factually incorrect, nonsensical, or not grounded in the provided context.

**Hash** - A fixed-size string or number generated from data using a hash function, used for data integrity and lookup.

**Heatmap** - A graphical representation of data where values are depicted by color, often used to show density or intensity.

**Hook** - A mechanism that allows custom code to be executed at specific points in a software lifecycle or process.

## I

**Idempotent** - An operation that produces the same result regardless of how many times it is executed with the same input.

**Imperative** - A programming paradigm that uses statements to change a program's state, focusing on how to achieve results.

**Incident Response** - The organized approach to addressing and managing the aftermath of a security breach or cyberattack.

**Infrastructure as Code (IaC)** - The practice of managing and provisioning computing infrastructure through machine-readable definition files.

**Integration Testing** - Testing phase where individual software modules are combined and tested as a group.

## J

**Jenkins** - An open-source automation server that enables developers to build, test, and deploy their software.

**Jira** - A proprietary issue tracking product developed by Atlassian that allows bug tracking and agile project management.

**JSON (JavaScript Object Notation)** - A lightweight data-interchange format that is easy for humans to read and write and easy for machines to parse and generate.

**Jailbreak** - Techniques or prompts designed to bypass an AI system's safety measures, ethical guidelines, or intended behavior constraints.

**JUnit** - A simple framework to write repeatable tests in Java, following the xUnit architecture for unit testing frameworks.

## K

**Kanban** - A visual workflow management method that helps visualize work, limit work-in-progress, and maximize efficiency.

**Kubernetes** - An open-source system for automating deployment, scaling, and management of containerized applications.

**Key Performance Indicator (KPI)** - A measurable value that demonstrates how effectively an organization is achieving key business objectives.

**Knowledge Distillation** - A technique where a smaller model (student) is trained to replicate the behavior of a larger model (teacher).

## L

**Latency** - The time delay between the cause and the effect of a physical change in the system being observed.

**Layer** - In software architecture, a level of abstraction that groups related functionality.

**Load Testing** - A type of performance testing that determines how a system behaves under both normal and anticipated peak load conditions.

**Log Aggregation** - The process of collecting log data from multiple sources and consolidating it for analysis and storage.

**Logical Unit** - A self-contained piece of work that can be understood, tested, and verified independently.

## M

**Microservices** - An architectural style that structures an application as a collection of loosely coupled services.

**Mock** - A simulated object that mimics the behavior of real objects in controlled ways, typically used in testing.

**Model Drift** - The degradation of model performance over time due to changes in the real-world environment and data.

**Monitoring** - The continuous observation and tracking of system performance, health, and behavior.

**Mutation Testing** - A method of software testing where certain statements of the source code are changed/mutated to check if the test cases are able to find the errors.

## N

**Natural Language Processing (NLP)** - A branch of artificial intelligence that helps computers understand, interpret and manipulate human language.

**Non-deterministic** - Producing different outputs even with the same input due to randomness, concurrency, or external factors.

**Normalization** - The process of organizing data in a database to reduce redundancy and improve data integrity.

**Notification** - An automated message or alert sent to inform users or systems about specific events or conditions.

**N+1 Query Problem** - A performance anti-pattern where a data access strategy executes N additional SQL statements to fetch the same data that could have been retrieved with fewer queries.

## O

**Observability** - The ability to infer the internal state of a system from its external outputs, primarily through logs, metrics, and traces.

**Orchestration** - The automated arrangement, coordination, and management of complex computer systems, middleware, and services.

**Outcome** - The result or consequence of an action, process, or event, particularly in the context of testing and evaluation.

**Overfitting** - A modeling error that occurs when a function is too closely fit to a limited set of data points, reducing its ability to generalize.

## P

**Pair Programming** - An agile software development technique where two programmers work together at one workstation.

**Pipeline** - A set of automated processes that allow developers and DevOps professionals to reliably and efficiently compile, build, and deploy their code.

**Policy as Code** - The practice of managing and enforcing policies through machine-readable and executable code rather than manual processes.

**Portability** - The ability of software to run on different hardware, operating systems, or environments with minimal or no modification.

**Precondition** - A condition that must be true before a specific section of code or test step can execute.

**Probabilistic** - Involving or exhibiting randomness; outcomes are described in terms of probabilities rather than certainties.

**Profiling** - The process of measuring the space or time complexity of a program, the usage of particular instructions, or the frequency and duration of function calls.

## Q

**Quality Assurance (QA)** - A way of preventing mistakes and defects in manufactured products and avoiding problems when delivering products or services to customers.

**Quantization** - The process of mapping input values from a large set to output values in a smaller set, often used to reduce model size and increase inference speed.

**Query** - A request for data or information from a database or other data source.

**Race Condition** - A situation where the behavior of software depends on the sequence or timing of uncontrollable events.

**Regression Testing** - A type of software testing that ensures that previously developed and tested software still performs correctly after it is changed or interfaced with other software.

**Release Candidate (RC)** - A beta version of software that is potentially ready to become a final product, ready to release unless significant bugs emerge.

## R

**RAG (Retrieval-Augmented Generation)** - An AI framework that combines information retrieval with text generation to enhance the accuracy and reliability of generated responses.

**Race Condition** - A flaw that occurs when multiple processes access and manipulate shared data concurrently, and the outcome depends on the timing of their execution.

**Refactoring** - The process of restructuring existing computer code without changing its external behavior to improve nonfunctional attributes.

**Regression** - A return to a former or less developed state; in software, when a previously working feature stops working after changes.

**Resilience** - The capacity to recover quickly from difficulties; in systems, the ability to withstand and recover from disruptions.

**Root Cause Analysis (RCA)** - A method of problem-solving used for identifying the root causes of faults or problems.

**Runbook** - A documented procedure for regularly occurring IT processes or for handling specific situations.

## S

**Selenium** - A portable framework for testing web applications that provides a playback tool for authoring functional tests without the need to learn a test scripting language.

**Service Level Agreement (SLA)** - A commitment between a service provider and a client that particular aspects of the service will meet certain standards.

**Service Level Indicator (SLI)** - A carefully defined quantitative measure of some aspect of the level of service that is provided.

**Service Level Objective (SLO)** - A target value or range of values for a service level that is measured by an SLI.

**Shift Left** - The practice of moving testing, quality, and performance evaluation earlier in the development lifecycle.

**Smoke Testing** - Preliminary testing to reveal simple failures severe enough to reject a prospective software release.

**Snapshot** - A copy of the state of a system at a particular point in time, often used for backup or comparison purposes.

**Spike** - In agile development, a time-boxed period used to research a concept or create a simple prototype.

**Static Code Analysis** - The analysis of computer software that is performed without actually executing programs.

**Stress Testing** - A form of testing that is used to determine the stability of a given system or entity under extreme conditions.

**Synthetic Monitoring** - Monitoring that uses scripted simulations of user behavior to test application performance and availability.

**System Under Test (SUT)** - The specific component, system, or piece of code that is being tested in a particular test scenario.

## T

**Test Double** - A generic term for any case where you replace a production object for testing purposes.

**Test Harness** - A collection of software and test data configured to test a program unit by running it under varying conditions.

**Test Suite** - A collection of test cases that are intended to be used to test a software program to show that it has some specified set of behaviors.

**Throttling** - The process of limiting the number of requests or the amount of data that can be sent or received within a fixed time interval.

**Trace** - A record of the execution path of a request through a distributed system, showing the timing and relationships between components.

**Trunk-Based Development** - A source-control branching model where developers collaborate on code in a single branch called 'trunk' or 'main'.

**Type Hint** - In Python, a way to indicate the expected data type of variables, function parameters, and return values.

## U

**Unit Testing** - A software testing method by which individual units of source code are tested to determine whether they are fit for use.

**User Acceptance Testing (UAT)** - The last phase of the software testing process where actual users test the software to make sure it can handle required tasks in real-world scenarios.

**Usability Testing** - A technique used in user-centered interaction design to evaluate a product by testing it on users.

**User Story** - An informal, natural language description of one or more features of a software system, written from the perspective of an end user.

## V

**Validation** - The process of checking that something meets a certain standard or requirement, especially in the context of data or models.

**Version Control** - A system that records changes to a file or set of files over time so that you can recall specific versions later.

**Virtual Environment** - A tool that helps to keep dependencies required by different projects separate by creating isolated python environments for them.

**Vulnerability** - A weakness which can be exploited by a threat actor, such as an attacker, to perform unauthorized actions within a computer system.

## W

**White Box Testing** - A method of software testing that tests internal structures or workings of an application, as opposed to its functionality.

**Workflow** - An orchestrated and repeatable pattern of business activity enabled by the systematic organization of resources into processes.

**Watchdog** - A timer that triggers a system reset or other corrective action if the main program, due to some condition, fails to service the timer before it reaches zero.

**Webhook** - A way for an app to provide other applications with real-time information by sending HTTP POST requests to a configured URL.

## X

**XML (eXtensible Markup Language)** - A markup language that defines a set of rules for encoding documents in a format that is both human-readable and machine-readable.

**XPath** - A query language for selecting nodes from an XML document.

**XSS (Cross-Site Scripting)** - A type of security vulnerability typically found in web applications that enables attackers to inject client-side scripts into web pages viewed by other users.

## Y

**YAML (YAML Ain't Markup Language)** - A human-readable data serialization standard that can be used in conjunction with all programming languages and is often used for configuration files.

**Yield** - In programming, a keyword that is used like a return statement, except that the function will return a generator.

## Z

**Zero Trust** - A security concept centered on the belief that organizations should not automatically trust anything inside or outside its perimeters and instead must verify anything and everything trying to connect to its systems before granting access.

**Zombie Process** - A process that has completed execution but still has an entry in the process table, allowing the parent process to read its child's exit status.

**Zone File** - A file containing instructions for resolving Internet domain names to Internet Protocol (IP) addresses.
