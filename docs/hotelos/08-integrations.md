# 08. Integrations and Connectors

## Supported integration domains
1. Payments
2. OTA/channel manager
3. Messaging (email/SMS/WhatsApp)
4. Accounting/BI exports
5. Identity/SSO

## Connector framework requirements
- Common interface for auth, sync, retry, and health.
- Provider-specific adapter implementation.
- Certification test suite before production enablement.
- Feature flags for phased rollout.

## Operational design
- Pull and push sync support.
- Conflict resolution strategy for external updates.
- Idempotent ingestion and dedupe by external references.

## Reliability and support
- Provider SLA metadata and alert thresholds.
- Playbooks for degraded providers.
- Manual reconciliation tools for failed sync batches.

## Security requirements
- Secret rotation and least-privilege credentials.
- Signed webhook verification.

Connector API conventions: [API Standards](./06-api-standards.md). Incident handling: [Operations/SRE](./12-operations-sre.md).
