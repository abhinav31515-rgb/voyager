# 03. Personas and User Journeys

## Core personas
1. **Front Desk Agent** — speed, clarity, low error tolerance.
2. **Reservations Manager** — booking modifications and guest requests.
3. **Revenue Manager** — pricing and occupancy optimization.
4. **Housekeeping Supervisor** — room readiness and SLA compliance.
5. **Marketing Content Manager** — offers, pages, campaigns.
6. **Owner/GM** — portfolio KPI and exception visibility.

Permission boundaries in [Security](./07-data-governance-security-compliance.md).

## Priority user journeys
### J1: Reservation create/modify/cancel
- Search availability → quote → hold → confirm payment → send confirmation.
- Failure modes: inventory race conditions, payment timeouts.

### J2: Day-of-arrival operations
- Pre-arrival list → room readiness → check-in decisions → key handoff.
- Failure modes: room not ready, guest mismatch, pending payment.

### J3: Revenue operations
- Update base rates/restrictions by date window and segment.
- Failure modes: conflicting overrides, accidental stop-sell.

### J4: Housekeeping orchestration
- Assign tasks by priority/SLA and update room state in real-time.

### J5: Publish campaign landing page
- Create localized offer page and attach booking widget.

## UX requirements by journey
- Wizards for high-risk operations.
- Inline validation + undo for destructive actions.
- Role dashboards with “today + exceptions”.

Design standards in [UI/UX](./09-ui-ux-guidelines.md). API dependencies in [API standards](./06-api-standards.md).
