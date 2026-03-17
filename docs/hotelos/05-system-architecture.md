# 05. System Architecture

## High-level architecture
- Multi-tenant Laravel backend
- PostgreSQL primary data store
- Redis for cache and queues
- Worker services for async jobs
- Object storage for media
- Optional API gateway

## Package architecture
See package boundaries in [Implementation Plan](./10-implementation-plan.md).

## Design decisions
- API-first to support web, mobile, and partners.
- Event-driven integration for reliability.
- Plugin contracts for extensibility.

## Architecture constraints
- Tenant isolation is mandatory.
- Booking write path requires strong consistency controls.

Security constraints in [Security and Compliance](./07-data-governance-security-compliance.md).
