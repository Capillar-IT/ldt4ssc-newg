# Source Code & Technical Components

This folder contains open-source scripts, validators, integration adapters, and pointers to the technical components developed or integrated within the **NeWG+** pilot.

---

## Component Architecture & Openness Model

As specified in **Section 4.2 of the Application Form** and **Annex 5 of the Pilot Grant Agreement**, NeWG+ follows a differentiated openness model that guarantees zero vendor lock-in and full standards-based portability for cities:

| Component Layer | Technology & Standards | Accessibility / Location |
|---|---|---|
| **LDT Context & Semantic Layer** | **NGSI-LD**, **Smart Data Models (OMA-SDM)**, JSON-LD mappings | **Open Source / Open Licence** — schemas and adapters published in [`data-models/`](../data-models/) and `src/`. |
| **Data-Space & Governance Plane (`MIRA` / `SEAMWARE`)** | **FIWARE Data Space Connector**, **Eclipse Dataspace Components (EDC)**, **TM Forum / DCAT** catalogues, **ODRL / ABAC** policies, **OIDC + DID/VC (EUDI/eIDAS2)** | **Open Standards & Reusable Governance Templates** — documented open-source deployment path in **PD3** and **PD4**. |
| **H3 Smart Mesh & Simulation Layer** | Python / Go spatial indexing (**Uber H3**), Madrid Open Data live XML/KML ingestion (`informo.madrid.es`, `mc30.es`, `datos.madrid.es`), MILP/surrogate models | **Reusable Service Package & Open API Specs** — documented in [`docs/madrid-open-data-h3-smart-mesh.md`](../docs/madrid-open-data-h3-smart-mesh.md). |
| **Codogno 3D LDT & Corridor Observatory (`POLIMI`)** | **CesiumJS**, Context Broker, Python ML pipelines (ARPA Lombardia, TomTom, Sentinel-2, OSM) | Publicly accessible demonstrator at [`codogno-digital-twin.netlify.app`](https://codogno-digital-twin.netlify.app/). |
| **NeWG Operational Suite & Shelter Gateway (`capillar IT`)** | CoCo AI (WhatsApp B2B), Stocker WMS, ERP connectors, DPP event pipeline, Shelter Gateway | **Limited-Access / Proprietary Operational Core** with **openly documented REST / NGSI-LD interfaces** and export paths. |
