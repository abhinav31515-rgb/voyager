# 11. Testing, Quality Gates, and Release Management

## Test pyramid
- Unit tests for domain rules.
- Integration tests for API and persistence.
- Contract tests for connectors.
- E2E tests for critical user journeys.

## Quality gates
- Static analysis and linting.
- Security scanning (SCA/SAST).
- Coverage thresholds on critical modules.
- Migration and rollback rehearsal.

## Release model
- Semantic versioning by package.
- Changelog and deprecation notices.
- Staged rollout with canary tenants.

Operational readiness is tracked in [Operations/SRE](./12-operations-sre.md).
