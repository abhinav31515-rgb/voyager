# 11. Testing, Quality Gates, and Release Management

## Test strategy
- Unit tests for domain rules.
- Integration tests for API+DB+queue behavior.
- Contract tests for each connector provider.
- E2E scenario tests for top journeys.
- Security test suite (authz, tenancy, injection, abuse cases).

## Required release gates
- Static analysis + lint clean.
- Dependency vulnerability checks.
- Migration safety checks and rollback plan.
- SLO regression checks on canary tenant.

## Quality metrics
- Defect escape rate
- Change failure rate
- Mean recovery time
- Journey success rates

## Release model
- Semantic versioning per package.
- Changelog with migration notes.
- Canary release, then regional rollout.

## Post-release controls
- 24–48h heightened monitoring.
- Incident review for any Sev1/Sev2 issue.

Operational response docs: [Operations/SRE](./12-operations-sre.md).
