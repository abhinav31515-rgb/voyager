# 18. Gap Analysis and Closure Plan

## Purpose
This document identifies missing depth and coverage gaps in the HarborOS documentation suite and defines closure actions.

## Identified gaps and status

| Gap ID | Gap Description | Impact | Closure Action | Owner | Status |
|---|---|---|---|---|---|
| GAP-01 | Limited FR/NFR coverage detail | Scope ambiguity | Expanded PRD with FR-1..FR-10 and NFR set | Product | Closed |
| GAP-02 | Incomplete reliability patterns | Delivery risk | Added idempotency/outbox/circuit breaker guidance | Architecture | Closed |
| GAP-03 | Weak compliance operating model | Audit risk | Added governance cadence + required artifacts | Security | Closed |
| GAP-04 | Sparse testing and release gates | Quality risk | Added mandatory release gates and quality metrics | QA/Eng | Closed |
| GAP-05 | Missing runbook and incident depth | Ops risk | Added runbook minimum set + incident process | SRE | Closed |
| GAP-06 | Limited migration control detail | Cutover risk | Added dual-run, rollback, data checks | Implementation | Closed |
| GAP-07 | Missing explicit gap tracker itself | Governance risk | Created this gap plan and linked from index | PMO | Closed |

## Remaining open areas (next iteration)
- Detailed API schema examples per high-risk endpoint.
- Detailed role-permission matrix by module.
- Costed capacity model for projected tenant scale.
- Regional compliance variants (country-specific addenda).

## Closure governance
- Review monthly in architecture + product steering.
- Any new gap must include owner, due date, and dependency links.

Related docs: [PRD](./02-product-requirements.md), [Architecture](./05-system-architecture.md), [Security](./07-data-governance-security-compliance.md), [Testing](./11-testing-quality-release.md), [Operations](./12-operations-sre.md).
