# 06. API Standards and Contracts

## API style guide
- Prefix all routes by version (`/v1`).
- ISO-8601 timestamps, UTC storage.
- Standard error envelope (`code`, `message`, `details`, `correlation_id`).
- Cursor pagination for large datasets.

## Critical endpoint classes
- Availability search and quote
- Reservation create/amend/cancel/check-in/check-out
- Rate and restriction updates
- Task management endpoints
- Payment capture/refund endpoints

## Contract rules
- Additive changes are minor versions.
- Breaking changes require new major version + migration path.
- Deprecation windows: min 12 months.

## Security model
- OAuth/OIDC user auth.
- Scoped PAT/service tokens for integrations.
- Idempotency keys mandatory for booking/payment POST endpoints.

## Webhooks
- Signed payloads + replay protection.
- Delivery retry policy and dead-letter queue.
- Consumer guidance + schema registry.

Consumer onboarding and cutover details: [Migration Playbook](./15-migration-adoption.md).
