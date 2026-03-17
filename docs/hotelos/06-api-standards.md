# 06. API Standards and Contracts

## Principles
- Versioned endpoints (`/v1/...`).
- Idempotency keys for booking/payment writes.
- Pagination, filtering, and consistent error schema.
- Webhook signature verification.

## Resource groups
- Properties, Rooms, Inventory, Rates
- Reservations, Folios, Payments
- Guests, Tasks, Content
- Integrations, Webhooks, Reports

## Contract governance
- Backward-compatible minor updates.
- Breaking changes only in major API versions.
- 12-month deprecation window.

See [Migration Playbook](./15-migration-adoption.md).

## API security
- OAuth2/OIDC for user flows.
- Scoped service tokens for connectors.

Details in [Security](./07-data-governance-security-compliance.md).
