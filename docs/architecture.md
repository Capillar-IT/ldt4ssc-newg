# NeWG+ Differentiated Two-City Architecture

**NeWG+** interconnects two Local Digital Twins (LDTs) across complementary urban and territorial morphologies under **LDT4SSC Work Strand 1**:

1. **Madrid (*Market-to-City* Flagship)**: Large metropolitan wholesale-to-retail ecosystem anchored in **Mercamadrid** (Europe's largest fresh-food platform), **COMAPES / AEMPM / ADEPESCA**, **Mercado de Maravillas** (Madrid's flagship pilot municipal market and Smart Urban Space / EUI anchor for the city's 46-market network), and the **Madrid Capital Digital** infrastructure (*Gemelo de Gemelos / Twin-of-Twins*, *City OS*, *Smart Urban Spaces / EUIs*, and the *Mercamadrid / EDINT Data Space*).
2. **Codogno (*Territory-to-City* Agrifood Corridor Twin)**: A medium-sized municipality in Lombardy's dairy and agrifood basin operating an existing 3D Local Digital Twin in CesiumJS (engineered with **Politecnico di Milano — POLIMI**), extended with a lightweight agrifood-flow observatory, local H3 smart mesh, corridor simulation toward **Milano / Sogemi**, and an optional light NeWG shared-dispatch probe.

---

## 1. End-to-End 7-Step Operational & Digital Twin Flow

```mermaid
flowchart LR
    S1["1. Order Capture<br/>CoCo AI (WhatsApp) & B2B Catalogues"] --> S2["2. Preparation<br/>Stocker WMS, Inverse Picking & Weighing"]
    S2 --> S3["3. Identification<br/>Edge IoT, Service-Anchors & DPP Events"]
    S3 --> S4["4. Collaborative Logistics<br/>Multi-Temp Consolidation & Shared Routes"]
    S4 --> S5["5. Context & Smart Mesh<br/>H3 Spatial Mesh & Selective Ingestion"]
    S5 --> S6["6. Governed Data Services<br/>MIRA / InterFlux / Shelter Gateway"]
    S6 --> S7["7. LDT & Decision Support<br/>Madrid Twin-of-Twins & Codogno Corridor LDT"]
```

| Step | Function | Key Technical & Operational Actors | Municipal Areas Involved (Madrid) |
|---|---|---|---|
| **1. Order** | Multichannel order capture (WhatsApp voice/text/image via CoCo AI), delivery address & time-window selection. | Wholesalers, Retailers, HORECA, capillar IT | Commerce, Mobility |
| **2. Preparation** | Assisted warehouse picking (*Stocker*), batch/lot assignment (FIFO), weighing & ERP synchronisation. | Wholesalers, Stall Teams, capillar IT | Commerce, Madrid Salud |
| **3. Identification** | Edge IoT / QR / RFID reading at docks & checkpoints (*service-anchors*), cold-chain logging & DPP creation. | Stall Teams, EUI / IoT Teams, capillar IT | Digital Office (DGOD), Commerce, Madrid Salud |
| **4. Logistics** | Multi-species refrigerated consolidation, shared dispatch, DUM 360 curb loading & POD verification. | Logistics Operators, COMAPES, AEMPM, Markets | Digital Office, Commerce, Mobility, Madrid Salud, Environment |
| **5. Context** | H3 Smart Mesh spatial indexing, ETA/time-window risk estimation & selective external data activation (Green IT). | capillar IT, SEAMWARE, Mines Paris - PSL | Digital Office, Commerce, Mobility, Environment |
| **6. Data Services** | Governed data product publication via MIRA, InterFlux Shelter Gateway, ODRL/ABAC policies & EUDI Wallet ID. | capillar IT, SEAMWARE, Mobilities4EU, POLIMI | Digital Office & Data-Owning Units |
| **7. LDT & Decisions** | Service twin simulation, policy what-if scenarios, curb/corridor regulation & cross-city reuse. | capillar IT, Mines Paris - PSL, Codogno, POLIMI | Digital Office & Consuming Municipal Units |

---

## 2. Four-Layer Technical Stack

1. **Layer 1 — Operational Application & Edge Layer (`NeWG` + `Service-Anchors`)**:
   - **Onboarding-by-Service**: Low-digital-maturity SMEs adopt NeWG because it solves immediate operational friction (orders, stock, weighing, dispatch, ETA) without requiring standalone data-space connectors.
   - **Service-Anchors & Service-Corridors**: Physical and mobile checkpoints (docks, consignment lockers, loading bays, handheld readers, EV chargers) linked into auditable chains (*service corridors*) that preserve asset/device/batch identity and feed role-specific **Digital Product Passport (DPP) Views**.
2. **Layer 2 — Sovereign Governance & Data Space Bridge (`MIRA`, `InterFlux` & `SEAMWARE`)**:
   - **MIRA (*Minimum Interoperability Reference Architecture*) & Shelter Gateway**: Separates internal operational micro-permissions inside NeWG from outward inter-organisational sharing.
   - **FIWARE / EDC Data Space Components**: TM Forum / DCAT-compatible catalogues, OIDC + DID/VC and EUDI/eIDAS2 wallet-compatible organisational identity, and **ODRL policies enforced via ABAC** (acting as a SIMPL-aligned Governance Authority Agent).
3. **Layer 3 — Context & Simulation Intelligence (`H3 Smart Mesh` — Mines Paris-PSL & capillar IT)**:
   - Spatial indexing over Uber H3 hexagonal cells combining operational events with city context (traffic, street closures, DUM 360 curb occupancy, air quality, EV/PV energy profiles).
   - **Eco-Design / Green IT Meta-Optimization**: External data feeds (FCD/telco, high-frequency traffic) are activated selectively only in cells and time windows where marginal ETA/TW accuracy gains justify the extra data, compute, and energy cost (targeting 60–80% compute reduction vs. raw continuous streaming).
4. **Layer 4 — Interconnected Local Digital Twins (`Madrid Twin-of-Twins` ⇄ `Codogno Corridor LDT`)**:
   - **Madrid**: Publishes governed NGSI-LD entities and shared services (`Mercamadrid Flow Statistics`, `Governed Merchant Publication & Discovery`, `Route/ETA/Exception Service`, `Smart-Mesh Logistics Context Services`) into the EUI/City OS and *Gemelo de Gemelos*.
   - **Codogno**: Reuses the service-corridor and smart-mesh methodology in a simulation-first medium-city environment (**CesiumJS** + POLIMI simulation engine), delivering 4 bounded shared services:
     1. *Fresh Corridor Context Service*
     2. *Producer Dispatch Planning Service*
     3. *Urban Loading & Access Service*
     4. *Scenario Pack (Before/After)*

---

## 3. OASC MIMs Plus Alignment (`MIM0`–`MIM8`)

| MIM Plus | Baseline Level | Target Level | Implementation in NeWG+ |
|---|---|---|---|
| **MIM0 — Accessing Data** | Partial | **Full** | API-first access to market, city, and shared services via FIWARE/EDC-compatible endpoints. |
| **MIM1 — Interlinking Data** | Partial | **Full** | NGSI-LD relationships connecting orders, batches, `ServiceAnchor`, `ServiceCorridor`, and H3 cells. |
| **MIM2 — Representing Data** | Partial | **Full** | Smart Data Models (OMA-SDM / NGSI-LD) and open model packs for logistics, corridors, and DPP views. |
| **MIM3 — Exchanging Data** | Partial | **Full** | Governed data products, TM Forum/DCAT catalogues, and policy-bound exchange via InterFlux/SEAMWARE. |
| **MIM4 — Personal Data** | Initial | **Partial** | Strict GDPR minimisation; role-based views and pseudonymisation across B2B and delivery workflows. |
| **MIM6 — Securing Data** | Partial | **Full** | OIDC, VC/DID (EUDI/eIDAS2 compatible), ODRL + ABAC enforcement, and auditable access logs. |
| **MIM7 — Geospatial Data** | Initial | **Partial/Full** | Uber H3 multi-resolution spatial mesh, corridor geometries, DUM curb/loading context, and GIS layers. |
| **MIM8 — Local Digital Twins** | Initial | **Partial/Full** | Federated interconnection of Madrid's *Twin-of-Twins* and Codogno's *Agrifood Corridor LDT*. |
