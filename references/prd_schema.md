# AI-Native PRD Output Schema

Use this schema when generating a full PRD for autonomous or semi-autonomous coding agents.

## Output contract

The PRD must be readable by humans and directly usable by coding agents. Use explicit IDs.

ID prefixes:

| Prefix | Meaning |
|---|---|
| `GOAL-` | product or business goal |
| `NOGOAL-` | non-goal |
| `TERM-` | glossary term |
| `JOURNEY-` | user journey |
| `STORY-` | AI-ready user story |
| `FR-` | functional requirement |
| `NFR-` | non-functional requirement |
| `DATA-` | data model item |
| `API-` | API/interface requirement |
| `ARCH-` | architecture constraint |
| `SEC-` | security/privacy/compliance requirement |
| `SUS-` | sustainability/GreenOps requirement |
| `CTX-` | context engineering artifact |
| `PHASE-` | implementation phase |
| `TASK-` | atomic implementation task |
| `AC-` | acceptance criterion |
| `TEST-` | test requirement |
| `OBS-` | observability requirement |
| `RISK-` | risk |
| `ROLLBACK-` | rollback/checkpoint item |
| `DOD-` | Definition of Done item |

---

# [Product / Feature Name] - AI-Native PRD

## 1. Executive Summary

```text
Purpose:
Target users:
Business objective:
Implementation approach:
Primary constraints:
Current readiness:
```

Include:
- one-paragraph summary,
- implementation-readiness status,
- top 3 risks,
- top 3 missing items.

## 2. Problem Statement

```text
Problem:
Who experiences it:
Current pain:
Cost of not solving:
Why now:
```

Rules:
- Do not describe only a feature gap.
- Define pain, workflow friction, or business impact.
- Mark unknown business claims as `MISSING`.

## 3. Goals and Non-Goals

### Goals

| ID | Goal | Metric / verification | Source |
|---|---|---|---|
| GOAL-001 |  |  | user-provided / ASSUMPTION |

### Non-Goals

| ID | Non-goal | Rationale |
|---|---|---|
| NOGOAL-001 |  |  |

## 4. Stakeholders and Users

| Role | Type | Needs | Permissions | Success criteria |
|---|---|---|---|---|
|  | stakeholder / user / admin / system |  |  |  |

## 5. Definitions and Domain Glossary

| ID | Term | Definition | Notes |
|---|---|---|---|
| TERM-001 |  |  |  |

## 6. Assumptions, MISSING, Open Questions

### Assumptions

| ID | Assumption | Reason | Validation method |
|---|---|---|---|
| ASSUMPTION-001 |  |  |  |

### MISSING

| ID | Missing information | Why it matters | Required before |
|---|---|---|---|
| MISSING-001 |  |  | implementation / architecture / security review |

### Open Questions

| ID | Question | Owner | Decision needed by |
|---|---|---|---|
| OPEN-001 |  |  |  |

### Blockers

| ID | Blocker | Impact | Resolution path |
|---|---|---|---|
| BLOCKER-001 |  |  |  |

## 7. Product Scope

### In scope

| ID | Scope item | Notes |
|---|---|---|
| SCOPE-001 |  |  |

### Out of scope

| ID | Out-of-scope item | Rationale |
|---|---|---|
| OUT-001 |  |  |

## 8. User Journeys

Use this format:

```text
JOURNEY-[number]: [name]
Actor:
Goal:
Preconditions:
Main path:
Alternative paths:
Failure paths:
Data touched:
Security implications:
Acceptance link:
```

## 9. AI-ready User Stories

Use this exact structure per story:

```text
STORY-[number]: [short title]
Actor:
Intent:
Business value:
Preconditions:
Trigger:
Given/When/Then:
  - Given [state/context]
    When [action/event]
    Then [verifiable result]
Input examples:
  - Input:
    Expected output:
Technical constraints:
NFR links:
Edge cases:
Failure modes:
Test ideas:
Dependencies:
```

## 10. Functional Requirements

| ID | Requirement | Verification | Dependencies |
|---|---|---|---|
| FR-001 |  | AC- / TEST- |  |

Functional requirement rules:
- Use imperative, testable statements.
- Define behavior, not implementation preference, unless architecture constraint requires it.
- Each data write must define validation and failure behavior.

## 11. Non-Functional Requirements

| ID | Category | Requirement | Target | Verification |
|---|---|---|---|---|
| NFR-001 | performance |  |  | TEST- |
| NFR-002 | reliability |  |  | TEST- |
| NFR-003 | accessibility |  |  | TEST- |
| NFR-004 | maintainability |  |  | review |
| NFR-005 | scalability |  |  | test/review |

If target is unknown, write `MISSING: target threshold`.

## 12. Data Model and Core Entities

Use this structure per entity:

```text
DATA-[number]: [EntityName]
Purpose:
Fields:
  - name:
    type:
    required:
    validation:
    default:
    sensitive:
Relationships:
Indexes:
Permissions:
Lifecycle states:
Retention:
Deletion/anonymization:
Migration notes:
Audit requirements:
Open questions:
```

Required fields for every entity:
- primary identifier,
- ownership or tenancy boundary,
- timestamps if lifecycle matters,
- authorization-relevant fields,
- validation rules.

## 13. API / Interface Requirements

Use this structure per API/interface:

```text
API-[number]: [name]
Type: REST / GraphQL / event / CLI / function / UI contract / webhook / other
Consumer:
Provider:
Authorization:
Request schema:
Response schema:
Error schema:
Validation:
Rate limits:
Idempotency:
Side effects:
Observability:
Test requirements:
```

## 14. Architecture Constraints

### Architecture summary

```text
Architecture style:
Primary layers:
Dependency direction:
Module boundaries:
Persistence boundary:
Integration boundary:
Configuration boundary:
Testing boundary:
```

### Constraints

| ID | Constraint | Rationale | Verification |
|---|---|---|---|
| ARCH-001 | Domain logic must not depend on infrastructure adapters. | Preserves testability and dependency inversion. | review + tests |
| ARCH-002 | External services must be accessed through interfaces/ports. | Allows mocks, retries, fallback, replacement. | review + tests |
| ARCH-003 | Validation, persistence, business logic, and presentation must be separate. | Enforces SRP. | review |
| ARCH-004 | Feature work must prefer vertical slices with bounded module changes. | Limits agent drift and coupling. | review |
| ARCH-005 | No uncontrolled global mutable state. | Prevents hidden coupling and nondeterminism. | review + tests |

## 15. Security, Privacy and Compliance

### Data classification

| Data type | Sensitivity | Storage | Retention | Logging allowed |
|---|---|---|---|---|
|  | public/internal/confidential/restricted |  |  | yes/no/redacted |

### Authorization matrix

| Actor | Resource | Create | Read | Update | Delete | Notes |
|---|---|---:|---:|---:|---:|---|
|  |  |  |  |  |  |  |

### Security requirements

| ID | Requirement | Verification |
|---|---|---|
| SEC-001 | Secrets must be loaded from approved configuration/secrets manager only. | review |
| SEC-002 | Sensitive values must not be logged. | test + review |
| SEC-003 | Protected resource access must check authorization server-side. | integration/security test |
| SEC-004 | Inputs must be validated at trust boundaries. | unit/integration test |
| SEC-005 | Destructive actions require authorization and rollback strategy. | review + test |

### Abuse cases

| ID | Abuse case | Mitigation | Test |
|---|---|---|---|
| ABUSE-001 |  |  | TEST- |

## 16. Sustainability and GreenOps

| ID | Requirement | Rationale | Verification |
|---|---|---|---|
| SUS-001 | Core list/search operations must define expected complexity. | Avoids accidental high-cost implementations. | review |
| SUS-002 | Expensive repeated reads must use caching where correctness permits. | Reduces I/O and infrastructure cost. | test/review |
| SUS-003 | Background jobs must have purpose, schedule, retry limits, and stop conditions. | Avoids zombie workloads. | review |
| SUS-004 | Agent handoff must reference stable docs instead of repeating large context. | Reduces token and inference cost. | review |
| SUS-005 | Indexes must be defined for expected high-volume queries. | Reduces database load. | review |

## 17. Context Engineering Artifacts

List recommended or generated artifacts:

| ID | File | Purpose | Status |
|---|---|---|---|
| CTX-001 | AGENTS.md | Agent operating instructions | recommended / generated |
| CTX-002 | .cursorrules | Cursor-specific rules or compatibility layer | recommended / generated |
| CTX-003 | llms.txt | LLM-facing documentation map | recommended / generated |
| CTX-004 | llms-full.txt | Full context bundle for agents | recommended / generated |
| CTX-005 | docs/architecture/adr-0001.md | Architecture decision record | recommended / generated |
| CTX-006 | docs/testing/test-strategy.md | Test strategy | recommended / generated |
| CTX-007 | docs/security/secrets-management.md | Secrets and security policy | recommended / generated |

## 18. Implementation Phases

Use the five-phase default unless project context requires another structure.

```text
PHASE-1: Foundation
Objective:
Includes:
Dependencies:
Exit criteria:
Validation commands:
Human review:

PHASE-2: Core Logic
Objective:
Includes:
Dependencies:
Exit criteria:
Validation commands:
Human review:

PHASE-3: Integration
Objective:
Includes:
Dependencies:
Exit criteria:
Validation commands:
Human review:

PHASE-4: UI/UX and State Management
Objective:
Includes:
Dependencies:
Exit criteria:
Validation commands:
Human review:

PHASE-5: Refinement
Objective:
Includes:
Dependencies:
Exit criteria:
Validation commands:
Human review:
```

## 19. Atomic Task Breakdown

Use this exact task format:

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

Task rules:
- One task should fit into one focused agent session.
- Do not mix schema, UI, API, and external integration in one task unless the slice is intentionally small.
- Each task must identify files or module boundaries.
- Each task must include a validation command or a `MISSING: validation command` marker.

## 20. Acceptance Criteria

| ID | Requirement/story | Given | When | Then | Verification |
|---|---|---|---|---|---|
| AC-001 | STORY-001 |  |  |  | TEST- |

## 21. Test Strategy

### Test matrix

| ID | Type | Scope | Requirement links | Tool/command | Required before |
|---|---|---|---|---|---|
| TEST-001 | unit | domain rule | FR- |  | PHASE- |
| TEST-002 | integration | persistence/API | API- |  | PHASE- |
| TEST-003 | contract | external service | API- |  | PHASE- |
| TEST-004 | e2e | user journey | JOURNEY- |  | PHASE- |
| TEST-005 | security | authorization/input | SEC- |  | PHASE- |
| TEST-006 | performance | latency/load | NFR- |  | PHASE- |
| TEST-007 | sustainability | resource/cost | SUS- |  | PHASE- |

## 22. Observability and Monitoring

| ID | Signal | Purpose | Location | Alert threshold |
|---|---|---|---|---|
| OBS-001 | structured log |  |  |  |
| OBS-002 | metric |  |  |  |
| OBS-003 | trace/span |  |  |  |
| OBS-004 | audit event |  |  |  |

Rules:
- Do not log secrets or sensitive personal data.
- Include correlation IDs where distributed behavior exists.
- Include failure metrics for external integrations.

## 23. Risk Register

| ID | Risk | Category | Likelihood | Impact | Mitigation | Owner |
|---|---|---|---|---|---|---|
| RISK-001 |  | product/tech/security/data/sustainability/agent | low/medium/high | low/medium/high |  |  |

Include agent-specific risks:
- agent drift,
- over-broad file edits,
- invented schemas,
- hidden coupling,
- insufficient tests,
- unsafe migrations.

## 24. Rollback and Checkpoints

| ID | Checkpoint | Rollback strategy | Human review required |
|---|---|---|---|
| ROLLBACK-001 | before migration |  | yes |
| ROLLBACK-002 | before external integration activation |  | yes |
| ROLLBACK-003 | before production release |  | yes |

## 25. Definition of Done

| ID | Done criterion | Verification |
|---|---|---|
| DOD-001 | All critical acceptance criteria pass. | test report |
| DOD-002 | Architecture constraints reviewed. | review checklist |
| DOD-003 | Security requirements reviewed. | security checklist |
| DOD-004 | Sustainability requirements reviewed. | GreenOps checklist |
| DOD-005 | Rollback plan tested or reviewed. | review/test |
| DOD-006 | Agent handoff instructions updated. | file review |
| DOD-007 | No unresolved BLOCKER remains. | PRD review |

## 26. Agent Handoff Instructions

Use this section as a pasteable block for coding agents.

```text
You are implementing according to this PRD. Treat the PRD as the single source of truth.

Active phase:
Allowed scope:
Files/modules allowed:
Files/modules prohibited:
Architecture constraints:
Security constraints:
Sustainability constraints:
Tests to run:
Validation commands:
Expected outputs:
Commit hints:
Rollback hints:
Stop and ask before:
  - changing data model beyond PRD
  - bypassing authorization
  - introducing new dependencies
  - moving business logic into UI/infrastructure
  - editing unrelated files
  - creating background jobs not specified
  - logging sensitive data
  - performing destructive migrations
Questions before implementation:
  - [list]
```

## Final PRD Quality Checklist

Before returning the PRD, verify:

- [ ] All mandatory sections exist.
- [ ] Unknowns are labeled.
- [ ] No central requirement is vague prose only.
- [ ] Data model is explicit or marked `MISSING`.
- [ ] API/interface contracts are explicit or marked `MISSING`.
- [ ] Architecture constraints are actionable.
- [ ] Security rules are actionable.
- [ ] Sustainability rules are actionable.
- [ ] Phases have exit criteria.
- [ ] Tasks are atomic and sequenced.
- [ ] Acceptance criteria are verifiable.
- [ ] Tests map to requirements.
- [ ] Rollback and checkpoints exist.
- [ ] Agent handoff is pasteable.
