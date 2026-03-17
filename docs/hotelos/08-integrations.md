# 08. Integrations and Connectors

## Connector categories
1. Payment gateways
2. OTA/channel manager adapters
3. Messaging providers (email/SMS/WhatsApp)
4. Accounting and BI exports

## Connector contract
- Standard auth lifecycle
- Health checks and rate limiting
- Retry/backoff policy
- Dead-letter queue support
- Certification test suite required for production approval

Operational policy: [Operations/SRE](./12-operations-sre.md).

## Data consistency model
- Outbound events are durable and replayable.
- External booking references must remain immutable links.

See [Domain Model](./04-domain-model.md).
