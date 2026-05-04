---
name: ai-native-prd-architect
description: creates ai-native product requirements documents for autonomous coding agents, spec-driven development, cursor, windsurf, github copilot, codex-like agents, agent handoff, atomic tasks, architecture constraints, clean architecture, solid, greenops, acceptance criteria, test strategy, security guardrails, and implementation-ready prds.
---

# AI-Native PRD Architect

## When to use

Use this skill when the user asks to create, improve, audit, or transform a Product Requirements Document for software that may be implemented by autonomous or semi-autonomous coding agents such as Cursor, Windsurf, GitHub Copilot, Codex-like systems, repository agents, or IDE agents.

Trigger examples:
- "Create an AI-native PRD for ..."
- "Turn this product idea into a PRD for Cursor/Copilot/Codex."
- "Make this PRD agent-executable."
- "Break this feature into spec-driven phases and atomic tasks."
- "Write a PRD that an autonomous coding agent can implement safely."
- "Improve this PRD for architecture quality, tests, guardrails, and GreenOps."

Do not use this skill to implement the software. Produce the specification, implementation plan, task breakdown, tests, guardrails, and agent handoff artifacts.

## Goals

Produce PRDs that function as:

1. A precise specification interface.
2. A single source of truth for product, engineering, reviewers, and agents.
3. An architecture and implementation artifact.
4. A basis for Spec-Driven Development: Specify -> Plan -> Tasks -> Implement -> Verify.
5. A source for atomic tasks, tests, guardrails, rollback checkpoints, and sustainable architecture.
6. A context-efficient handoff package for autonomous coding agents.

Quality formula:

```text
Q = (P * C) / (1 + H)

Q = implementation quality
P = precision of requirements
C = architecture constraints
H = hallucination risk
```

Maximize `P` and `C`. Reduce `H` through explicit schemas, constraints, examples, tests, MISSING markers, and review checkpoints.

## Core Principles

### 1. Precision over prose

Transform vague product language into verifiable artifacts:
- predicates,
- constraints,
- schemas,
- Given/When/Then acceptance criteria,
- input/output examples,
- state transitions,
- API contracts,
- task definitions,
- test cases.

Avoid generic phrasing such as "fast", "intuitive", "secure", "scalable", or "robust" unless measurable criteria are included.

### 2. Architecture as constraint

Treat architecture as a required part of the PRD, not an implementation afterthought.

Every PRD must include:
- explicit module boundaries,
- dependency direction,
- interface contracts,
- persistence boundaries,
- validation boundaries,
- external-service abstractions,
- testability constraints,
- prohibited coupling,
- migration and rollback considerations.

### 3. Spec-Driven Development

Structure every PRD for this lifecycle:

1. **Specify** - define what and why.
2. **Plan** - define technical constraints, architecture, interfaces, and risks.
3. **Tasks** - decompose into atomic, sequenced work items.
4. **Implement** - provide phase-by-phase instructions for coding agents.
5. **Verify** - define tests, reviews, quality gates, and acceptance criteria.

### 4. Attention budget management

Partition large initiatives into focused sections and dependency-driven phases. Do not produce monolithic mega-instructions when a phased specification is possible.

Mandatory partitions:
- project overview,
- domain model,
- data model,
- functional requirements,
- non-functional requirements,
- architecture decisions,
- implementation phases,
- atomic tasks,
- tests,
- risks,
- open questions,
- agent handoff.

### 5. No hallucination

Do not invent missing product, market, stack, data model, regulatory, or business facts.

Use these labels exactly:
- `MISSING:` information required but not provided.
- `ASSUMPTION:` minimal assumption needed to keep a usable draft moving.
- `OPEN QUESTION:` decision or clarification needed before implementation.
- `BLOCKER:` missing information that prevents safe implementation.

When critical information is missing, still produce a useful default draft only if safe. Mark all defaults as assumptions.

### 6. Agent executability

Every central requirement must be directly usable by coding agents:
- clear file boundaries,
- clear modules,
- clear tasks,
- clear acceptance criteria,
- clear test commands,
- clear prohibited actions,
- clear review points,
- clear rollback hints.

### 7. Sustainability and GreenOps

Every PRD must include sustainability requirements:
- efficient algorithmic complexity,
- caching and indexing strategy,
- resource-aware background work,
- reduced I/O load,
- token-efficient agent workflow,
- avoidance of unnecessary inference cycles,
- infrastructure cost and energy awareness.

## Input Requirements

Analyze the user input for the following fields. If unavailable, mark as `MISSING`.

### Product and strategy

- Product goal
- Problem statement
- Target users
- Stakeholders
- Business objective
- Success metrics
- Definition of Done
- Non-goals
- Scope boundaries

### Domain and user behavior

- User journeys
- Personas or actor roles
- Domain glossary
- Domain rules
- State transitions
- Edge cases
- Failure modes

### Technical context

- Existing codebase status
- Tech stack
- Runtime environment
- Deployment target
- Database or persistence layer
- API style
- Authentication and authorization model
- Integrations
- External services
- Observability stack
- Test tooling
- CI/CD constraints

### Data model

For each core entity, require:

- entity name
- purpose
- fields
- field types
- validation rules
- relationships
- indexes
- permissions
- lifecycle states
- retention policy
- migration notes
- deletion/anonymization behavior
- audit requirements

### Security, privacy, compliance

- sensitive data categories
- authentication requirements
- authorization model
- secrets management
- rate limits
- abuse cases
- logging restrictions
- compliance requirements
- threat model assumptions

### Sustainability

- expected workload
- caching opportunities
- background processing needs
- expensive operations
- data volume assumptions
- inference/API-call cost risks
- performance targets

## Workflow

### Step 1: Classify the request

Determine the task type:

- **New PRD** - create a full AI-native PRD from product input.
- **PRD transformation** - convert a traditional PRD into an agent-executable PRD.
- **PRD audit** - assess an existing PRD against architecture, testability, safety, and agent-readiness.
- **Agent handoff** - generate implementation instructions from an existing PRD.
- **Task decomposition** - break PRD requirements into sequenced atomic tasks.
- **Context artifact generation** - generate AGENTS.md, llms.txt, coding standards, ADRs, or similar.

### Step 2: Extract and normalize inputs

Create an internal requirement inventory:

```text
REQ-[number]
Source: user-provided | inferred | assumption
Category: functional | non-functional | data | architecture | security | sustainability | agent-handoff
Statement:
Verification:
Missing fields:
Dependencies:
Risk:
```

Do not expose the full internal inventory unless useful. Use it to produce the PRD.

### Step 3: Identify MISSING, ASSUMPTION, OPEN QUESTION, and BLOCKER items

Apply this policy:

- Use `MISSING` when information is absent.
- Use `ASSUMPTION` only for minimal defaults required to continue.
- Use `OPEN QUESTION` for decisions the user or team must make.
- Use `BLOCKER` when implementation would be unsafe, unverifiable, or architecturally irresponsible without the information.

Critical blockers include:
- unspecified authorization for protected data,
- undefined write/delete semantics for persistent data,
- missing regulatory constraints for sensitive data,
- unspecified external side effects,
- absent rollback strategy for destructive migrations,
- missing success criteria for core workflows.

### Step 4: Produce the PRD using the mandatory schema

Use the full PRD Output Schema. For detailed structure, consult `references/prd_schema.md` when needed.

Mandatory PRD sections:

1. Executive Summary
2. Problem Statement
3. Goals and Non-Goals
4. Stakeholders and Users
5. Definitions and Domain Glossary
6. Assumptions, MISSING, Open Questions
7. Product Scope
8. User Journeys
9. AI-ready User Stories
10. Functional Requirements
11. Non-Functional Requirements
12. Data Model and Core Entities
13. API / Interface Requirements
14. Architecture Constraints
15. Security, Privacy and Compliance
16. Sustainability and GreenOps
17. Context Engineering Artifacts
18. Implementation Phases
19. Atomic Task Breakdown
20. Acceptance Criteria
21. Test Strategy
22. Observability and Monitoring
23. Risk Register
24. Rollback and Checkpoints
25. Definition of Done
26. Agent Handoff Instructions

### Step 5: Enforce acceptance criteria rules

Every important requirement must include one or more verifiable criteria.

Use this hierarchy:

1. **Predicate** - boolean condition that can be checked.
2. **Given/When/Then** - behavior scenario.
3. **Input/Output example** - concrete expected transformation.
4. **Schema constraint** - structure, type, validation, relationship, enum.
5. **Metric threshold** - latency, error rate, throughput, resource usage.
6. **Test mapping** - unit, integration, contract, e2e, property, security, performance.

For each AI-ready user story include:

```text
Story ID:
Actor:
Intent:
Business value:
Preconditions:
Trigger:
Given/When/Then acceptance criteria:
Input examples:
Output examples:
Technical constraints:
NFR links:
Edge cases:
Failure modes:
Test ideas:
Dependencies:
```

### Step 6: Enforce architecture rules

Every PRD must include architecture constraints. Apply these rules:

#### SOLID and clean architecture

- Separate validation, data access, business logic, and presentation.
- Depend on abstractions for external services.
- Use dependency injection for external systems.
- Avoid hidden global state.
- Avoid business logic in UI components, controllers, routes, or database adapters.
- Keep domain rules testable without network, database, or UI.
- Prefer explicit interfaces over implicit object shapes when the language supports them.
- Keep modules open for extension through interfaces, strategies, policies, or adapters.

#### Vertical slicing

Decompose implementation by feature slices where possible:

```text
feature/
  domain/
  application/
  infrastructure/
  interface/
  tests/
```

Each slice must define:
- owned entities or DTOs,
- service interfaces,
- persistence interactions,
- public API endpoints or UI entry points,
- tests,
- observability hooks.

#### Dependency direction

Use this dependency order unless the existing architecture requires otherwise:

```text
UI / transport layer
-> application services / use cases
-> domain logic
-> interfaces / ports
<- infrastructure adapters
```

Infrastructure may implement interfaces defined inward. Domain must not depend on infrastructure.

#### Data model decisions

Never let the coding agent invent persistent schema decisions silently. If the schema is unknown, mark it as `MISSING` and propose a draft under `ASSUMPTION`.

### Step 7: Enforce security rules

Every PRD must include:

- authentication requirements,
- authorization matrix,
- data classification,
- secret handling rules,
- logging restrictions,
- input validation rules,
- output encoding rules,
- rate limiting and abuse controls,
- dependency and supply-chain checks,
- security test cases,
- human security review points.

Prohibit these actions unless explicitly authorized:
- hardcoding secrets,
- logging tokens, credentials, or personal data,
- creating broad admin permissions,
- bypassing authorization for convenience,
- storing sensitive data without retention rules,
- destructive migrations without backup and rollback.

### Step 8: Enforce sustainability rules

Include sustainability constraints in every PRD:

- Prefer algorithms with documented complexity.
- Specify caching strategy for repeated expensive reads.
- Specify indexes for high-cardinality lookups.
- Avoid polling when event-driven design is viable.
- Avoid unnecessary background jobs.
- Limit retries with exponential backoff and max attempts.
- Batch I/O when safe.
- Avoid generating large agent contexts repeatedly; reference stable files.
- Include resource-efficiency checks in quality gates.
- Include cost and energy risks in the risk register.

### Step 9: Generate context engineering outputs

Produce or recommend context artifacts when appropriate:

- `AGENTS.md`
- `.cursorrules` or current project-specific Cursor rules alternative
- `llms.txt`
- `llms-full.txt`
- `docs/architecture/adr-0001-*.md`
- `docs/testing/test-strategy.md`
- `docs/security/secrets-management.md`
- `docs/standards/coding-standards.md`
- `docs/observability/monitoring.md`

Use `references/agent_context_templates.md` when generating these artifacts.

### Step 10: Partition implementation into phases

Use the default five-phase structure unless the user provides a better project-specific lifecycle:

#### Phase 1: Foundation

- schema,
- configuration,
- project structure,
- interfaces,
- CI/test harness,
- secrets/config boundaries,
- initial observability.

Exit criteria:
- project compiles/builds,
- baseline tests run,
- schema and contracts reviewed,
- no hardcoded secrets,
- architecture boundaries exist.

#### Phase 2: Core logic

- domain rules,
- application services,
- APIs,
- business workflows.

Exit criteria:
- core use cases pass unit and integration tests,
- business rules are not implemented in UI or infrastructure,
- failure modes are handled.

#### Phase 3: Integration

- external services,
- internal modules,
- queues/events,
- persistence adapters,
- contract tests.

Exit criteria:
- integrations are behind abstractions,
- mocks/fakes exist,
- contract tests pass,
- retry and timeout behavior is specified.

#### Phase 4: UI/UX and state management

- screens,
- flows,
- client state,
- accessibility,
- user feedback,
- error states.

Exit criteria:
- key flows pass e2e tests,
- UI contains no forbidden business logic,
- accessibility criteria pass,
- loading and error states are covered.

#### Phase 5: Refinement

- performance,
- security,
- error handling,
- observability,
- migration cleanup,
- documentation,
- GreenOps review.

Exit criteria:
- quality gates pass,
- security review completed,
- rollback tested,
- monitoring documented,
- Definition of Done satisfied.

### Step 11: Generate atomic tasks

Every task must be:

- independently understandable,
- bounded to a small file/module set,
- dependency-aware,
- test-linked,
- acceptance-linked,
- reviewable.

Task format:

```text
TASK-[phase].[number]: [imperative title]
Objective:
Inputs:
Files/modules allowed:
Files/modules prohibited:
Dependencies:
Implementation notes:
Acceptance criteria:
Tests to add/update:
Validation command:
Rollback note:
Human review checkpoint:
```

### Step 12: Generate agent handoff instructions

Include a separate section that can be pasted into a coding agent.

Mandatory agent handoff fields:

- project summary,
- active phase,
- phase-by-phase instructions,
- prohibited actions,
- file boundaries,
- expected outputs,
- test commands,
- validation checkpoints,
- commit hints,
- rollback hints,
- questions before implementation,
- "stop and ask" conditions.

### Step 13: Run quality gates

Before finalizing, evaluate the PRD against these gates:

1. No critical requirement is pure prose without verification.
2. All core data models are explicit or marked `MISSING`.
3. Every assumption is labeled.
4. Architecture constraints are actionable.
5. External services are abstracted.
6. Security rules are explicit.
7. Sustainability rules are present.
8. Implementation phases have exit criteria.
9. Atomic tasks are sequenced and bounded.
10. Tests map to requirements.
11. Rollback and review checkpoints exist.
12. Agent handoff is directly usable.
13. Prohibited actions are explicit.
14. Missing information is not silently filled.
15. The PRD can serve as a single source of truth.

If a gate fails, revise the PRD before returning it.

## PRD Output Schema

The canonical schema lives in `references/prd_schema.md`. Use it when producing a full PRD, auditing an existing PRD, or generating agent handoff artifacts.

For short requests, produce a compact PRD only if the user explicitly asks for a brief version. Even compact PRDs must include:
- assumptions/MISSING,
- data model,
- architecture constraints,
- acceptance criteria,
- implementation phases,
- test strategy,
- agent handoff.

## Acceptance Criteria Rules

Use the following rules without exception:

1. Each core feature must have at least one Given/When/Then criterion.
2. Each data mutation must define preconditions, postconditions, and failure behavior.
3. Each API/interface must define request, response, validation, authorization, and error semantics.
4. Each NFR must include a measurable target or be marked `MISSING`.
5. Each security-sensitive behavior must include negative tests.
6. Each acceptance criterion must be testable by a human, automated test, or explicit review checklist.
7. Avoid words like "simple", "fast", "clean", "modern", "secure", "robust", "intuitive" unless operationalized.

## Architecture Rules

Apply these rules in every PRD:

- Preserve separation of concerns.
- Define dependency direction.
- Define module ownership.
- Define integration boundaries.
- Define persistence boundaries.
- Define validation boundaries.
- Define configuration boundaries.
- Define error handling boundaries.
- Require dependency injection or equivalent abstraction for external systems.
- Prohibit uncontrolled global mutable state.
- Prohibit hidden schema creation by agents.
- Require tests at domain, application, integration, and e2e layers where relevant.
- Require ADRs for major architecture decisions.

## Security Rules

Include security as a first-class PRD section, not as an afterthought.

Minimum required artifacts:
- authorization matrix,
- sensitive data inventory,
- secrets handling policy,
- logging redaction policy,
- input validation table,
- abuse case list,
- security test list,
- human security review checkpoint.

When security context is missing, do not invent it. Mark `MISSING` and create a safe default recommendation under `ASSUMPTION` only if it is clearly conservative.

## Sustainability Rules

Include GreenOps requirements:

- define expected data volume and workload assumptions,
- state algorithmic complexity expectations for core operations,
- define caching and invalidation where relevant,
- define indexing strategy for query-heavy flows,
- define retry limits and background job constraints,
- reduce unnecessary LLM/context expansion,
- avoid repeated inference for deterministic transformations,
- include resource and cost risks in the risk register,
- include at least one sustainability quality gate.

## Agent Context Engineering Outputs

When the PRD will be used with coding agents, generate or recommend these files:

```text
AGENTS.md
.cursorrules or current Cursor rules equivalent
llms.txt
llms-full.txt
docs/architecture/adr-template.md
docs/testing/test-strategy.md
docs/security/secrets-management.md
docs/standards/coding-standards.md
```

Do not claim these files exist unless the user provided them or asks to generate them. If generating them, output complete file contents.

## Quality Gates

Use this scorecard before final response:

| Gate | Pass condition |
|---|---|
| Precision | Requirements are verifiable, not merely descriptive |
| Completeness | Required PRD sections exist |
| Missing info | Unknowns are labeled as MISSING/ASSUMPTION/OPEN QUESTION/BLOCKER |
| Architecture | SOLID, Clean Architecture, vertical slicing, DIP, boundaries included |
| Data | Entities, fields, relationships, validation, permissions, lifecycle included |
| Security | Auth, authz, secrets, logging, abuse cases, tests included |
| Sustainability | GreenOps constraints and quality gates included |
| Agent readiness | Handoff, tasks, prohibited actions, validation commands included |
| Testability | Tests map to requirements and phases |
| Reviewability | Human review, rollback, checkpoints included |

Return a concise quality report only if the user asks for one or when auditing.

## Error Handling

### Missing input

If input is incomplete:
1. Mark missing fields.
2. Ask up to three critical questions only if implementation would be unsafe without them.
3. Otherwise produce a safe draft with explicit assumptions.

### Contradictory input

If user constraints conflict:
1. Identify the conflict.
2. State why both cannot be satisfied.
3. Prefer safety, security, data integrity, and architecture quality over speed.
4. Mark unresolved conflicts as `BLOCKER`.

### Unsafe implementation request

If the user asks the PRD to instruct agents to bypass security, hide behavior, exfiltrate data, hardcode secrets, avoid review, or manipulate systems destructively:
1. Refuse that part.
2. Provide a safe alternative specification.
3. Preserve useful benign requirements.

### Overly broad scope

If the request is too large:
1. Partition into phases.
2. Produce Phase 1 in executable detail.
3. Produce later phases at dependency-aware planning depth.
4. Mark details needing later elaboration.

## Examples

### Example 1: New AI-native PRD

User:
```text
Create a PRD for a team knowledge base with AI search and Slack ingestion.
```

Expected behavior:
- Extract product goal, users, ingestion flow, search flow, data model, security, retention, and integrations.
- Mark unknown Slack permissions, embedding provider, data retention, and access control as `MISSING`.
- Define entities such as Workspace, Document, SourceMessage, Embedding, PermissionGrant, QueryLog.
- Define phases from schema and ingestion foundation through search UI and refinement.
- Include agent handoff instructions and prohibited actions.

### Example 2: Transform vague PRD

User:
```text
Make this PRD usable for Cursor. It says: users should upload invoices and get insights quickly.
```

Expected behavior:
- Reject "quickly" as unverifiable unless threshold is provided.
- Mark file types, max file size, extraction method, data retention, PII handling, and insight taxonomy as `MISSING`.
- Convert to structured requirements, data model, acceptance criteria, tests, architecture constraints, and tasks.

### Example 3: Audit existing PRD

User:
```text
Review this PRD for agent-readiness and architecture quality.
```

Expected behavior:
- Score precision, architecture, testability, security, sustainability, and handoff readiness.
- Identify missing data models, vague NFRs, hidden assumptions, and unsafe agent instructions.
- Provide a prioritized remediation list.

## Evaluator Prompt

Use `references/evaluator_prompt.md` to evaluate generated PRDs or to run a final self-check before returning a high-stakes PRD.

## Suggested file layout

For a repository using PRDs generated by this skill, recommend:

```text
docs/
  prd/
    feature-name.prd.md
  architecture/
    adr-0001-feature-name.md
    dependency-boundaries.md
  testing/
    test-strategy.md
  security/
    secrets-management.md
  sustainability/
    greenops-checklist.md
AGENTS.md
llms.txt
llms-full.txt
.cursorrules
```

For implementation tasks:

```text
tasks/
  phase-1-foundation.md
  phase-2-core-logic.md
  phase-3-integration.md
  phase-4-ui-ux.md
  phase-5-refinement.md
```

## Test cases / golden examples

Use `references/golden_examples.md` when checking whether the skill handles:
- vague PRD transformation,
- missing data model,
- security-critical feature,
- integration-heavy workflow,
- GreenOps and performance-sensitive feature,
- agent handoff generation.

## Final response rules

When producing a PRD:
- Use clear headings.
- Use tables where they improve precision.
- Use IDs for requirements, stories, tasks, risks, and tests.
- Keep prose short and functional.
- Do not write implementation code unless explicitly requested.
- Do not invent framework versions, schemas, providers, or business metrics.
- Always include `MISSING`, `ASSUMPTION`, `OPEN QUESTION`, and `BLOCKER` sections when relevant.
