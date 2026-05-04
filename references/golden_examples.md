# Golden Examples and Test Cases

Use these examples to test whether the skill produces AI-native PRDs rather than traditional stakeholder prose.

## Golden Example 1: Vague product idea

### Input

```text
Create a PRD for an app where freelancers can send invoices and see insights quickly.
```

### Expected behavior

The skill must not accept "quickly" as sufficient.

Expected output characteristics:
- `MISSING: supported invoice formats`
- `MISSING: latency target for insights`
- `MISSING: storage and retention policy`
- `MISSING: payment provider, if payments are included`
- `MISSING: authentication and authorization model`
- `ASSUMPTION: invoices are uploaded as PDF unless specified otherwise`
- Data entities such as `User`, `Invoice`, `InvoiceLineItem`, `Insight`, `UploadedFile`, `AuditEvent`
- Given/When/Then criteria for upload, parsing, validation, insight display, and failure handling
- Security requirements for invoice data
- Sustainability requirements for avoiding repeated parsing and using caching
- Phased implementation with schema before UI

### Failure modes

Fail if:
- output says "fast insights" without threshold or MISSING marker,
- data model is absent,
- security section is generic only,
- tasks tell the agent to "build the app" in one step.

## Golden Example 2: Traditional PRD transformation

### Input

```text
Transform this into an AI-native PRD:

Users should manage team documents. They can upload, organize, and search files. The interface should be clean and search should be smart.
```

### Expected behavior

The skill must convert vague wording into structured artifacts.

Required MISSING markers:
- file types and max file size,
- folder/tag model,
- search backend or retrieval method,
- permissions model,
- retention policy,
- definition of "smart search",
- latency and relevance metrics.

Required architecture constraints:
- document parsing behind interface,
- search provider behind interface,
- domain logic separated from UI,
- metadata persistence separated from blob storage,
- authorization checks on every document read.

Required acceptance criteria:
- upload success,
- unsupported file rejection,
- permission-restricted search result exclusion,
- empty search result behavior,
- search latency target marked MISSING if unknown.

## Golden Example 3: Security-sensitive feature

### Input

```text
Write a PRD for admin impersonation so support can debug customer accounts.
```

### Expected behavior

The skill must treat this as security-sensitive.

Required sections:
- threat model notes,
- authorization matrix,
- audit logging,
- explicit approval workflow,
- time-limited impersonation,
- no password/token access,
- user-visible or compliance-driven notification policy marked MISSING if not provided,
- rollback/revocation behavior,
- abuse cases,
- security tests.

Required prohibited actions:
- do not expose user secrets,
- do not bypass audit logging,
- do not allow broad admin access without scope,
- do not log sensitive data.

Fail if:
- PRD optimizes only support convenience,
- no abuse cases,
- no audit requirements,
- no human security review checkpoint.

## Golden Example 4: Integration-heavy workflow

### Input

```text
Create an AI-native PRD for syncing CRM contacts to our product database and sending lifecycle emails.
```

### Expected behavior

Required MISSING markers:
- CRM provider,
- email provider,
- source-of-truth rules,
- conflict resolution,
- unsubscribe/compliance requirements,
- sync frequency,
- retry and idempotency behavior.

Required architecture:
- CRM adapter interface,
- email provider interface,
- sync orchestration service,
- idempotency keys,
- job state table,
- dead-letter or failure tracking,
- rate-limit handling.

Required GreenOps:
- avoid excessive polling,
- batch sync where safe,
- cache provider metadata,
- retry limits,
- monitor job duration and failure rate.

## Golden Example 5: Performance and sustainability

### Input

```text
Make a PRD for recommendations on a content platform.
```

### Expected behavior

Required MISSING markers:
- recommendation goal,
- available signals,
- ranking criteria,
- freshness requirements,
- scale assumptions,
- latency target,
- model/provider constraints.

Required sustainability requirements:
- avoid recomputing recommendations on every page load unless necessary,
- define caching window,
- batch or precompute where appropriate,
- define cost/resource budget as MISSING if not provided,
- measure recommendation latency and cache hit rate.

Required tests:
- deterministic ranking test for rules-based baseline,
- fallback behavior test,
- performance test,
- privacy test for excluded/private content.

## Golden Example 6: Agent handoff only

### Input

```text
Generate agent handoff instructions from this PRD.
```

### Expected behavior

The skill must produce a pasteable handoff block with:
- active phase,
- allowed files/modules,
- prohibited files/modules,
- architecture constraints,
- security constraints,
- sustainability constraints,
- tests to run,
- validation commands,
- expected outputs,
- commit hints,
- rollback hints,
- stop-and-ask conditions.

Fail if:
- handoff is generic,
- no prohibited actions,
- no test commands or MISSING marker,
- no stop-and-ask conditions.

## Golden Example 7: PRD audit

### Input

```text
Audit this PRD for autonomous implementation readiness.
```

### Expected behavior

The skill must produce:
- scorecard,
- P0/P1/P2 revision list,
- missing information,
- agent drift risks,
- architecture risks,
- security risks,
- sustainability risks,
- recommendation to block implementation if critical gates fail.

Fail if:
- it only summarizes the PRD,
- it does not identify implementation risks,
- it does not distinguish missing facts from assumptions.

## Regression checklist

A generated PRD passes if:

- It contains all 26 mandatory PRD sections or explicitly states that the user requested a compact version.
- It uses requirement IDs.
- It includes `MISSING` markers.
- It does not invent stack versions.
- It includes explicit data models.
- It includes architecture constraints.
- It includes security constraints.
- It includes GreenOps constraints.
- It includes phased implementation.
- It includes atomic tasks.
- It includes acceptance criteria.
- It includes test strategy.
- It includes rollback and checkpoints.
- It includes pasteable agent handoff.
