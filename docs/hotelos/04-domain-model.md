# 04. Domain Model and Bounded Contexts

## Contexts
- Core/Tenancy
- Inventory
- Rates
- Reservations
- Guest CRM
- Operations
- Content
- Payments
- Channels
- Analytics

## Core entities
- Tenant, Property, RoomType, RoomUnit
- RatePlan, Restriction, Promotion
- Reservation, StaySegment, Folio, Payment, Refund
- Guest, ConsentRecord
- HousekeepingTask, MaintenanceTicket
- IntegrationCredential, WebhookDelivery, AuditLog

See [API contracts](./06-api-standards.md) and [Integrations](./08-integrations.md).

## Domain events (examples)
- ReservationCreated
- ReservationModified
- RatePlanUpdated
- RoomStatusChanged
- PaymentCaptured

Operational handling in [Operations/SRE](./12-operations-sre.md).
