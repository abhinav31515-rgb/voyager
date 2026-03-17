# Voyager Commercial-Grade Assessment and Modernization Plan (2026)

> Note: A dedicated, cross-referenced commercial documentation suite is now available at [`docs/hotelos/README.md`](./hotelos/README.md).

## 1) Executive summary

Voyager is a Laravel admin panel package intended to accelerate back-office CRUD/BREAD development (Browse, Read, Edit, Add, Delete), with built-in media management, menu builder, settings, role/permission controls, and multilingual support.

From a business perspective, this project is now in **maintenance sunset**: the upstream README explicitly states the project is archived and no longer receiving updates. That changes the risk profile from "adopt and extend" to "stabilize short-term, then migrate or fork with strong ownership".

### Commercial verdict

- **Best use case today:** legacy admin back office that needs short-term continuity.
- **Risk level for net-new enterprise adoption:** high, due to archived lifecycle, older UI stack, and mixed dependency posture.
- **Recommended strategy:** run a two-track plan:
  1. **Hardening + usability uplift** for current users (3–8 weeks)
  2. **Modern platform migration/fork strategy** (3–9 months)

---

## 2) What this project is made for

Voyager is positioned as:

- An admin interface for Laravel apps
- A BREAD generator over database models/tables
- Menu, media, settings, and role management

It is explicitly **not** a complete CMS or blog platform by default.

**Business implication:** Voyager is a productivity layer for operations/admin teams, not a full product framework.

---

## 3) Current product and technical posture

### 3.1 Lifecycle and support posture

- The upstream project marks itself archived and suggests alternatives (Wave, Filament, Genesis, Nova/starter kits).
- This is a major strategic signal: no dependable upstream patch cadence for future CVEs, framework shifts, or browser/runtime changes.

### 3.2 Architecture snapshot

The package is a classic Laravel package architecture:

- Service-provider centric bootstrapping
- Route registration in a dedicated Voyager routes file
- Large controller-driven backend logic for BREAD workflows
- Blade templates for server-rendered admin UI
- Frontend assets built with Laravel Mix + Webpack, Vue 2, Bootstrap 3, and jQuery ecosystem plugins

### 3.3 Scalability and maintainability observations

- Some classes are highly consolidated (e.g., >1000-line base controller), which increases onboarding cost and regression risk.
- Dynamic route generation based on database `DataType` rows is flexible but couples runtime DB state with route shape, complicating static analysis and operational predictability.
- Heavy plugin-based frontend stack raises long-term UI consistency and accessibility costs.

---

## 4) Dependency and platform audit

### 4.1 Backend platform compatibility

- Composer constraints currently allow Laravel 8/9/10/11 and PHP up to 8.3.
- Documentation pages still mention Laravel 8/9 prerequisites, showing documentation drift relative to package constraints.

**Risk:** confusion during implementation and support handoffs.

### 4.2 Frontend/runtime aging indicators

Core frontend dependencies include:

- Vue 2.x
- Bootstrap 3.x
- jQuery ecosystem + older plugin family
- Laravel Mix/Webpack pipeline

`npm outdated` confirms multiple packages behind latest major versions (e.g., Bootstrap 3 vs latest 5, Vue 2 vs latest 3, DataTables 1 vs 2, TinyMCE 6 vs 8).

**Risk:** increasing breakage probability with modern browsers/toolchains and harder hiring/onboarding due to dated stack choices.

### 4.3 Test and CI posture

- Test workflows exist and include matrix testing across PHP/Laravel versions.
- CI uses older action versions and Node 16 in workflows.
- Local PHP test execution requires vendor dependencies (not present in this environment), so operational confidence depends on CI and downstream integrator setups.

---

## 5) Commercial limitations and conflict analysis

### 5.1 Product-market conflicts

1. **Legacy admin UX vs non-technical users**
   - The current UI paradigm is admin-centric and developer-configured; non-technical content teams increasingly expect guided workflows, guardrails, autosave, and role-based simplified surfaces.

2. **Configuration depth vs ease-of-use**
   - High flexibility (BREAD/config-driven behavior) can overwhelm non-technical teams without opinionated defaults and templates.

3. **Archived upstream vs enterprise procurement**
   - Security/compliance teams may reject archived dependencies without a formal internal ownership model.

### 5.2 Technical conflicts

1. **Backward compatibility vs modernization velocity**
   - Supporting broad Laravel/PHP ranges slows architectural upgrades and code simplification.

2. **Dynamic route/database-driven structure vs typed/contract-first development**
   - Harder to apply strict static checks and predictable API governance.

3. **Monolithic controllers vs modular domain design**
   - Slower parallel team delivery and more regression hotspots.

---

## 6) What must change to be easy, modern, and effective for non-technical users

## Phase 0 (Immediate: 1–2 weeks) — Stabilize and de-risk

1. **Adopt explicit ownership model**
   - Decide: internal fork vs migration path to an actively maintained admin platform.
   - Create SLA for security patches and framework updates.

2. **Documentation correction pass**
   - Align docs with actual supported Laravel/PHP matrix.
   - Add explicit "supported browsers," "known limits," and upgrade policy.

3. **Security hygiene baseline**
   - Add automated dependency scanning (Composer + npm) in CI.
   - Add baseline SAST rules and minimum code quality gates.

## Phase 1 (Short term: 3–8 weeks) — Non-technical usability uplift

1. **Role-based simplified interfaces**
   - Introduce "task-based" admin modes (Content Editor, Catalog Manager, Support Agent).
   - Hide low-level config fields by default.

2. **Guided content workflows**
   - Add step-by-step create/edit wizards.
   - Draft/approval states, autosave, inline validation hints.

3. **Safer media UX**
   - Better file constraints feedback, upload progress reliability, and undo/restore flows.

4. **Accessibility and language improvements**
   - WCAG-targeted improvements (focus order, labels, contrast checks).
   - Improve translation coverage in admin strings.

## Phase 2 (Mid term: 2–4 months) — Architecture modernization

1. **Refactor controller hotspots**
   - Split massive base controller by concern (querying, actions, validation, media hooks, relationship orchestration).

2. **Introduce service layer + typed DTO/form requests**
   - Reduce controller complexity and increase testability.

3. **Formalize extension contracts**
   - Versioned plugin APIs for form fields/actions/events.

4. **Observability**
   - Add structured logs, audit trails for admin actions, and key usage telemetry.

## Phase 3 (Mid/long term: 3–6 months) — Frontend platform refresh

1. **Move from Webpack/Mix legacy setup toward Vite-first build**
2. **Migrate Vue 2 components to Vue 3 or Livewire/Inertia-based strategy**
3. **Replace Bootstrap 3 design system with modern, accessible component system**
4. **Reduce jQuery plugin surface; consolidate around maintained UI primitives**

## Phase 4 (Strategic: 6–9 months) — Productization for enterprise use

1. **Admin product packaging**
   - Opinionated starter templates by industry/use-case.

2. **Compliance features**
   - Immutable audit logs, granular permission analytics, data retention hooks.

3. **Operational supportability**
   - LTS policy, compatibility matrix, migration tooling, and deprecation governance.

---

## 7) Prioritized backlog (practical)

### P0 (now)

- Establish internal ownership and maintenance policy
- Correct docs/support matrix drift
- Add CI dependency/vulnerability checks
- Publish official "archived upstream" risk notice for stakeholders

### P1 (next)

- Build non-technical role profiles and guided forms
- Refactor top 2 complexity hotspots (`VoyagerBaseController`, media flow)
- Add end-to-end tests for critical admin journeys (login, BREAD CRUD, media upload)

### P2

- Frontend modernization program (design system + framework migration)
- Progressive decoupling from legacy plugin stack

---

## 8) Suggested target state (north star)

A modernized Voyager successor should provide:

- **User-first admin UX** for non-technical operators
- **Composable architecture** with clear extension boundaries
- **Observable + secure operations** suitable for compliance-heavy teams
- **Predictable upgrade path** with published LTS and migration tooling


---

## 9) New product direction: build our own hotel-first framework/package

Instead of extending Voyager incrementally, the better strategic move is to build a **new hotel operations framework** that is reusable across hotel websites, booking engines, and mobile apps.

Working name: **HarborOS** (placeholder).

### 9.1 Product thesis

Build a **multi-tenant, API-first hotel platform** that gives:

- A non-technical operations admin (staff-friendly)
- A website CMS + booking engine
- Partner APIs for apps, kiosks, and channel integrations
- Strong governance (audit, permissions, policy, compliance)

This should be a framework/package that can power:

1. Independent boutique hotel sites
2. Multi-property hotel groups
3. Travel partner booking surfaces
4. White-label deployments for agencies/SIs

### 9.2 What we are building (package boundaries)

Ship as modular packages under one ecosystem:

- `harbor/core` — tenancy, auth, roles, audit, settings, feature flags
- `harbor/inventory` — properties, room types, units, allotments, restrictions
- `harbor/rates` — rate plans, seasonal pricing, promo rules, contracts
- `harbor/reservations` — booking lifecycle, folios, refunds, modifications
- `harbor/guest` — profiles, consent, preferences, loyalty hooks
- `harbor/ops` — housekeeping, maintenance, shift tasks, SLA rules
- `harbor/content` — website CMS blocks, media, SEO, localization
- `harbor/payments` — gateway abstraction, tokenization, reconciliation
- `harbor/channels` — OTA/channel manager connectors and sync jobs
- `harbor/analytics` — KPI definitions (Occupancy, ADR, RevPAR), exports
- `harbor/sdk` — client SDKs (web, mobile), typed API contracts

### 9.3 Core architectural principles

1. **API-first + event-driven**
   - All business operations exposed via versioned APIs.
   - Domain events for reservations, rate updates, and room state changes.

2. **Tenant-safe by default**
   - Hard tenant scoping at data and query layers.
   - Per-tenant config, branding, policy, and integration credentials.

3. **Workflow-first UX for non-technical users**
   - Guided actions over raw CRUD screens.
   - Role dashboards with “today’s tasks” and “exceptions requiring action.”

4. **Extensibility over customization forks**
   - Plugin contracts for payment providers, channel connectors, and reports.
   - No direct core patching for customer-specific behavior.

5. **Observable and compliance-ready**
   - Immutable audit trails for rate, booking, refund, and permission changes.
   - Traceable background jobs and integration retries.

### 9.4 Functional scope (v1)

#### Reservation and front-office
- Availability search, quote, reserve, amend, cancel
- Check-in/check-out and room assignment
- No-show handling and waitlist rules

#### Revenue management basics
- Rate calendar editor with rule presets
- Length-of-stay restrictions (MinLOS/MaxLOS)
- Promotions and coupon windows

#### Operations and housekeeping
- Live room status board
- Cleaning and maintenance workflows
- Turnaround alerts for same-day arrivals

#### Website + booking engine
- Drag/drop page sections for offers and room pages
- Rate/availability widgets embeddable into websites
- Multi-language content and SEO metadata templates

#### Finance and controls
- Payment capture/void/refund workflows
- Folio line items and tax/service fee policies
- Daily reconciliation reports

### 9.5 Cross-platform strategy (web + apps)

- **Admin web app:** primary operations console
- **Guest-facing web components:** embeddable booking widgets
- **Staff mobile app APIs:** housekeeping and front desk task endpoints
- **Guest app APIs:** booking lookup, modification, check-in prep

All clients consume the same versioned domain APIs.

### 9.6 Reference tech stack

- Backend: Laravel 11/12 + PostgreSQL + Redis + queue workers
- API: REST first, optional GraphQL gateway for partner aggregation
- Admin UI: Filament or Vue 3/Inertia + design system tokens
- Infrastructure: containerized deploys, object storage, managed queue/cache
- Security: SSO/SAML/OIDC support, 2FA, scoped API keys, secret rotation

### 9.7 Data model backbone (minimum)

- Tenant, Property, Building, Floor
- RoomType, RoomUnit, InventoryBlock
- RatePlan, RateRule, Restriction, Promotion
- Reservation, StaySegment, Folio, Invoice, Payment, Refund
- Guest, ConsentRecord, Preference, LoyaltyAccount
- HousekeepingTask, MaintenanceTicket, Shift
- ChannelConnection, SyncJob, ExternalReservationRef
- AuditLog, WebhookDelivery, IntegrationCredential

### 9.8 Integration contracts (must-have)

1. Payment gateways (Stripe/Adyen/Razorpay abstractions)
2. Email/SMS/WhatsApp providers
3. OTA/channel sync adapters (pull+push)
4. Accounting export connectors (CSV/API)
5. Webhooks for downstream CRM/BI tools

Define strict connector interfaces and certification tests before onboarding each provider.

### 9.9 Product editions and monetization

- **Starter:** single property, core booking + website CMS
- **Growth:** multi-property, channel sync, advanced pricing rules
- **Enterprise:** SSO, audit exports, custom connectors, SLA and support tiers

Commercial model options:
- Subscription per property/month
- Usage add-ons (messages, transactions, channel volume)
- Setup/implementation services via partners

### 9.10 Delivery roadmap

#### Phase A (0–90 days): foundation MVP
- Tenant model, auth/roles, properties/rooms, reservations, basic payments
- Admin dashboard + booking workflow wizard
- Basic website content modules and booking widget

#### Phase B (90–180 days): operational maturity
- Housekeeping board, pricing calendar, reconciliation reports
- Connector SDK and first payment + messaging integrations
- Audit trails and role templates for non-technical staff

#### Phase C (6–12 months): platform scale
- Multi-property controls and portfolio analytics
- Channel/OTA connector framework and certification harness
- White-label toolkit and partner portal

### 9.11 Non-functional requirements (commercial grade)

- 99.9% monthly uptime target for core booking APIs
- Zero cross-tenant data leakage (mandatory tenancy tests)
- RPO/RTO targets defined per edition
- Full auditability of booking, pricing, and refund events
- Backward-compatible API version policy with deprecation windows

### 9.12 Go-to-market execution plan

1. Design partner cohort (3–5 hotels) for discovery + pilot
2. Ship narrow MVP with measurable operational KPIs
3. Build migration toolkit from legacy admin stacks
4. Publish implementation playbooks for agencies
5. Create certification program for integration partners

### 9.13 Key risks and mitigations

- **Risk:** Integration complexity explodes.
  - **Mitigation:** strict adapter contracts + sandbox certification suite.
- **Risk:** Staff adoption is weak.
  - **Mitigation:** workflow-first UX, role templates, in-app guided tours.
- **Risk:** Margin erosion from custom requests.
  - **Mitigation:** plugin architecture and paid extension model.
- **Risk:** Data/compliance incidents.
  - **Mitigation:** immutable audit logs, least-privilege defaults, security reviews.

### 9.14 Immediate next actions (next 2 weeks)

- Finalize product charter and package boundaries (`harbor/*`)
- Define v1 API contracts for reservations, inventory, and rates
- Produce clickable UX prototype for Front Desk + Reservations roles
- Stand up architecture spike repo (Laravel + tenancy + queue + audit)
- Select 2 payment providers and design adapter interfaces

