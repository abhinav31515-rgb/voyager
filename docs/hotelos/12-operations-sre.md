# 12. Operations, SRE, and Support Runbooks

## SLO/SLA baseline
- Booking API availability: 99.9% monthly.
- Payment operation success SLO by provider class.
- Queue processing lag thresholds by job type.

## Observability stack expectations
- Structured logs with tenant and correlation IDs.
- Metrics dashboards: booking funnel, payment health, sync health.
- Tracing on all external provider calls.

## Runbooks (minimum set)
- Reservation write-path degradation
- Payment gateway outage and fallback mode
- OTA/channel sync backlog and replay
- Housekeeping board stale-data recovery
- Tenant-level incident containment

## Incident management
- Severity matrix and on-call rotations.
- RACI for engineering, support, and product.
- Post-incident action item tracking.

## Capacity and DR
- Load-testing cadence.
- Backup verification and restore drills.
- RPO/RTO targets per edition.

Risk alignment: [Risk Register](./14-risk-register.md). Quality gates: [Testing](./11-testing-quality-release.md).
