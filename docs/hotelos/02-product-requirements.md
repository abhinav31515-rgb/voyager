# 02. Product Requirements (PRD)

## Problem statement
Hotels operate across disconnected systems, leading to slow operations, weak pricing control, and inconsistent guest communication.

## Product goals
- **G1:** Deliver role-based, workflow-first operations UI.
- **G2:** Expose stable APIs for websites, apps, and partner services.
- **G3:** Support multi-property tenancy with strong data isolation.
- **G4:** Enable commercial packaging (Starter/Growth/Enterprise).

Commercialization details: [Pricing and GTM](./13-commercial-pricing-gtm.md).

## Non-goals
- Full ERP replacement in v1.
- Deep accounting replacement; support export/integration instead.

## Functional requirements
- **FR-1** Property, room, and policy setup.
- **FR-2** Availability management and restrictions.
- **FR-3** Rate plans, promotions, and price overrides.
- **FR-4** Reservation lifecycle (create/modify/cancel/check-in/out).
- **FR-5** Guest profile, preferences, and consent records.
- **FR-6** Housekeeping and maintenance workflows.
- **FR-7** Website CMS and booking widgets.
- **FR-8** Payment workflows and reconciliation support.
- **FR-9** Integration connector framework.
- **FR-10** Reporting and KPI exports.
- **FR-11** Dynamic website modules (blog/news/notifications/page sections).

## Non-functional requirements
- **NFR-Sec:** RBAC, 2FA, immutable audit trail.
- **NFR-Rel:** 99.9% monthly availability for booking APIs.
- **NFR-Perf:** P95 API latency targets per endpoint class.
- **NFR-Data:** Zero cross-tenant leakage.
- **NFR-Oper:** Runbook coverage for Sev1/Sev2 incidents.
- **NFR-Cost:** Cost-to-serve controls by tenant tier.
- **NFR-NoOps:** Managed-platform operation with minimal dedicated infrastructure staffing.

## Acceptance criteria (v1)
- End-to-end booking flow passes E2E tests.
- Payment capture/refund tested with at least 2 providers.
- Rate changes audited and queryable.
- Housekeeping task board usable on tablet/mobile.
- Blog/news/notification modules publish dynamically without code changes.
- All FR/NFR mapped to tests and owners.

Traceability source of truth: [Traceability Matrix](./traceability-matrix.md) and [Testing](./11-testing-quality-release.md).

Cost and no-DevOps operating constraints are detailed in [Commercial Cost-Effective Blueprint](./19-commercial-grade-cost-effective-blueprint.md).
