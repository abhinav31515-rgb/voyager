# 05. System Architecture

## Logical architecture
- API/Application service layer (Laravel)
- Domain modules (`harbor/*`) with explicit contracts
- Persistence layer (PostgreSQL)
- Queue/event pipeline (Redis + workers)
- Object storage + CDN for media
- Integration gateway for external connectors

## Deployment model
- Multi-tenant SaaS baseline, optional dedicated tenancy for enterprise.
- Horizontal scaling for API and worker pools.
- Separate worker classes: reservations, payments, channels, notifications.

## Reliability patterns
- Idempotent writes for booking/payment operations.
- Outbox pattern for event publication.
- Retries with backoff and dead-letter queues.
- Circuit breakers for unstable third-party providers.

## Data and consistency strategy
- Strong consistency for reservation/payment write path.
- Eventual consistency for analytics and non-critical sync.

## Architecture decisions to document
- ADR-001: Tenancy model.
- ADR-002: Reservation conflict strategy.
- ADR-003: Integration retry/backoff policy.
- ADR-004: API versioning policy.

These decisions are validated by [Testing](./11-testing-quality-release.md) and monitored in [Operations/SRE](./12-operations-sre.md).
