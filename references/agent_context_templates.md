# Agent Context Engineering Templates

Use these templates when the user asks to generate repository context artifacts for coding agents.

## AGENTS.md Template

```md
# AGENTS.md

## Purpose

This repository is implemented according to the PRD located at:

```text
docs/prd/[feature-name].prd.md
```

Treat the PRD as the single source of truth.

## Operating Rules

1. Read the relevant PRD section before editing code.
2. Work only within the active phase and assigned task.
3. Do not invent data models, permissions, APIs, framework versions, or external providers.
4. Do not edit unrelated files.
5. Do not move business logic into UI, routes, controllers, database adapters, or external-service adapters.
6. Do not hardcode secrets.
7. Do not log sensitive data.
8. Do not perform destructive migrations without the PRD rollback plan.
9. Stop and ask if a required decision is marked `MISSING`, `OPEN QUESTION`, or `BLOCKER`.

## Architecture Rules

- Domain logic must be independent of infrastructure.
- External services must be accessed through interfaces or ports.
- Validation, data access, business logic, and presentation must be separated.
- Prefer vertical slices for feature implementation.
- Avoid uncontrolled global mutable state.

## Testing Rules

Before claiming completion, run:

```bash
MISSING: project-specific test command
```

Add or update tests linked to:
- acceptance criteria,
- domain rules,
- API/interface behavior,
- security rules,
- failure modes.

## Security Rules

- Load secrets from approved configuration only.
- Redact sensitive logs.
- Enforce authorization server-side.
- Validate all untrusted inputs at trust boundaries.
- Add negative tests for protected operations.

## Sustainability Rules

- Avoid unnecessary repeated computation.
- Use caching and indexing when specified by the PRD.
- Avoid unbounded background jobs.
- Respect retry limits and stop conditions.
- Keep agent context focused by referencing stable files instead of duplicating large documents.

## Completion Checklist

- [ ] Task acceptance criteria pass.
- [ ] Required tests pass.
- [ ] Architecture boundaries preserved.
- [ ] Security constraints satisfied.
- [ ] Sustainability constraints satisfied.
- [ ] Rollback notes updated if relevant.
- [ ] No unresolved BLOCKER remains.
```

## .cursorrules Template

```text
Follow docs/prd/[feature-name].prd.md as the source of truth.

Do not invent:
- schemas,
- providers,
- permissions,
- framework versions,
- file locations,
- environment variables.

Respect architecture:
- keep domain logic out of UI/routes/controllers/adapters,
- depend on abstractions for external services,
- separate validation, persistence, business logic, and presentation,
- avoid global mutable state,
- make each change within the assigned task and phase.

Before editing:
- identify the active PHASE and TASK,
- list files to modify,
- list tests to run,
- stop if the PRD marks required information as MISSING, OPEN QUESTION, or BLOCKER.

Before completion:
- run required tests,
- verify acceptance criteria,
- report files changed,
- report any unresolved assumptions.
```

## llms.txt Template

```text
# [Project Name]

## Source of truth

- PRD: docs/prd/[feature-name].prd.md
- Agent rules: AGENTS.md
- Architecture decisions: docs/architecture/
- Test strategy: docs/testing/test-strategy.md
- Security rules: docs/security/secrets-management.md

## Implementation phases

- Phase 1: Foundation
- Phase 2: Core Logic
- Phase 3: Integration
- Phase 4: UI/UX and State Management
- Phase 5: Refinement

## Agent usage

Use this file as a navigation map. Load only the documents relevant to the active task.
```

## llms-full.txt Template

```text
# [Project Name] Full Agent Context

## Load order

1. AGENTS.md
2. docs/prd/[feature-name].prd.md
3. docs/architecture/ relevant ADRs
4. docs/testing/test-strategy.md
5. docs/security/secrets-management.md
6. task file for the active phase

## Constraints

Do not duplicate this file into prompts unless needed. Prefer referencing stable files to reduce token usage and inference cost.
```

## ADR Template

```md
# ADR-[number]: [Decision Title]

## Status

Proposed / Accepted / Superseded

## Context

[What decision is needed and why.]

## Decision

[The chosen architecture decision.]

## Consequences

### Positive

-

### Negative

-

### Neutral / trade-offs

-

## Alternatives considered

| Alternative | Reason rejected |
|---|---|
|  |  |

## Links

- PRD: docs/prd/[feature-name].prd.md
- Requirements: ARCH- / FR- / NFR-
```

## Test Strategy Template

```md
# Test Strategy

## Scope

This test strategy covers the requirements in:

```text
docs/prd/[feature-name].prd.md
```

## Test matrix

| Test ID | Type | Requirement links | Command | Owner |
|---|---|---|---|---|
| TEST-001 | unit |  | MISSING |  |
| TEST-002 | integration |  | MISSING |  |
| TEST-003 | contract |  | MISSING |  |
| TEST-004 | e2e |  | MISSING |  |
| TEST-005 | security |  | MISSING |  |
| TEST-006 | performance |  | MISSING |  |
| TEST-007 | sustainability |  | MISSING |  |

## Completion rule

No task is complete until its linked acceptance criteria and required tests pass or are explicitly marked as blocked.
```

## Secrets Management Template

```md
# Secrets Management

## Rules

- Do not hardcode secrets.
- Do not commit `.env` files unless explicitly approved and sanitized.
- Load secrets from the approved runtime configuration or secrets manager.
- Redact secrets and sensitive personal data from logs.
- Rotate credentials if exposure is suspected.

## Required secret inventory

| Secret | Purpose | Runtime location | Rotation owner | Logging allowed |
|---|---|---|---|---|
| MISSING | MISSING | MISSING | MISSING | no |

## Agent stop conditions

Stop and ask before:
- adding a new secret,
- changing secret names,
- logging values from configuration,
- bypassing secret validation.
```

## Coding Standards Template

```md
# Coding Standards

## Module boundaries

- Domain logic belongs in domain modules.
- Application orchestration belongs in use-case/application modules.
- Persistence belongs in repositories/adapters.
- External service calls belong behind interfaces.
- UI renders state and triggers actions; it must not contain domain rules.

## Error handling

- Use explicit error types or equivalent structured error handling.
- Preserve user-safe error messages.
- Log diagnostic details without sensitive values.
- Include retry limits for transient external failures.

## Review checklist

- [ ] No unrelated files changed.
- [ ] No business logic placed in UI/infrastructure.
- [ ] No hidden global mutable state introduced.
- [ ] External services are abstracted.
- [ ] Tests cover success and failure paths.
- [ ] Security and sustainability constraints preserved.
```
