# Data Models (NGSI-LD & Smart Data Models)

This folder documents the **NGSI-LD / Smart Data Models (OMA-SDM)** and semantic mappings created or adapted by the **NeWG+** pilot under **LDT4SSC Work Strand 1** (engaging with **OASC MIM1 Interlinking Data**, **MIM2 Representing Data**, and **MIM7 Geospatial Data**).

All created or adapted data models and semantic mappings are published under open licences (`CC BY 4.0` / `Apache-2.0`) for reuse across the European LDT ecosystem.

---

## Planned Model Families

1. **Fresh-Food Logistics & Commercial Offer Models (`NGSI-LD / TM Forum / DCAT`)**:
   - Qualified fresh-offer catalogue items, discretionary stock availability, B2B order state, consolidated dispatch manifests, and route/ETA entities.
2. **Service-Anchor & Service-Corridor Entities (`ServiceAnchor`, `ServiceCorridor`)**:
   - Extends Madrid's Smart Urban Space (EUI) persistent-anchor logic beyond fixed points to represent docks, consignment lockers, loading bays, handheld checkpoints, EV charging bays, and ordered route corridors with auditable event histories.
3. **Digital Product Passport (DPP) Continuity & Role-Specific Passport Views**:
   - Complementary domain objects linking batch/lot origin, cold-chain temperature/humidity readings, handling/seal events, and Point-of-Delivery (POD) evidence into role- and purpose-bound views (Merchant, Logistics Operator, Market Manager, Health/Inspection Authority, and aggregated City LDT).
4. **H3 Smart-Mesh Context & Corridor Intelligence Entities**:
   - Multi-resolution Uber H3 cell state entities (Resolutions 8, 9, and 10) representing demand-per-cell, effective traversal speed, active street-closure penalties, DUM 360 curb/loading saturation probability, market node energy-readiness (PV generation / EV charging), and learned segment costs.

---

## Related Repositories

- **NeWG NGSI-LD Adapter & Mappings**: Internal repository (`newg-ngsi-ld`) — public schemas, JSON-LD `@context` definitions, and example payloads will be published in this folder as they are frozen in **PD3 (M3 — Pilot Scope & Architecture)**.
