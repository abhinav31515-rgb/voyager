# 04. Domain Model and Bounded Contexts

## Bounded contexts
- **Core:** Tenant, User, Role, FeatureFlag, AuditLog
- **Inventory:** Property, RoomType, RoomUnit, InventoryBlock
- **Rates:** RatePlan, RateRule, Restriction, Promotion
- **Reservations:** Reservation, StaySegment, Folio, Invoice
- **Payments:** PaymentIntent, Capture, Refund, Dispute
- **Guest:** Guest, Preference, ConsentRecord, LoyaltyLink
- **Operations:** HousekeepingTask, MaintenanceTicket, Shift
- **Content:** Page, Offer, MediaAsset, Translation
- **Channels:** ChannelConnection, Mapping, SyncJob, ExternalRef
- **Analytics:** MetricDefinition, Snapshot, DashboardConfig

## Key invariants
- Reservation total must equal folio + tax/service components.
- Room unit cannot be double-assigned for overlapping intervals.
- Tenant boundary is enforced on every aggregate query/write.
- Rate restrictions must be deterministic and conflict-resolved.

## Domain events
- ReservationCreated, ReservationUpdated, ReservationCancelled
- PaymentAuthorized, PaymentCaptured, RefundIssued
- RoomStatusChanged, HousekeepingTaskCompleted
- RatePlanPublished, RestrictionChanged
- OfferPublished

Event handling and reliability: [Operations/SRE](./12-operations-sre.md).

## Data lifecycle
- Hot operational data in OLTP store.
- Analytical snapshots in reporting store.
- Audit logs immutable and long retention.

Controls and legal alignment: [Security/Compliance](./07-data-governance-security-compliance.md).
