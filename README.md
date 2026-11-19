# NeWG+ — LDT4SSC Pilot Project Repository (Work Strand 1)

**New Wholesale Market Generation: cities digital infrastructure implementation through sustainable logistics and commerce**

This repository is the home of the **NeWG+ pilot project** under the European **LDT4SSC** (*Local Digital Twins for Smart and Sustainable Communities*, Work Strand 1 — Interconnecting Local Digital Twins). It contains the pilot's documentation, shared artefacts, data models, and ongoing journey updates, serving as the canonical public record of the pilot's work (`2026-08-31` to `2028-02-29`).

## Overview

**NeWG+** interconnects Madrid's *Market-to-City* flagship with Codogno's *Territory-to-City* Agrifood Corridor Twin across two complementary urban and territorial scales:

- **Madrid (Spain) — Market-to-City Flagship**: Anchored in **Mercamadrid** (Europe's largest fresh-food wholesale hub), **Mercado de Maravillas** (Madrid's flagship pilot municipal market, serving as a replicable blueprint for the city's 46-market network), and the **Madrid Capital Digital** strategy (Twin-of-Twins / *Gemelo de Gemelos*, City OS, Smart Urban Spaces / EUIs, and Municipal Data Space). Low-digital-maturity wholesalers, logistics operators, and B2B buyers adopt **NeWG** for daily operations (catalogues, orders, stock, dispatch, routes, ETA, and Digital Product Passport continuity), generating governed data products via **MIRA & InterFlux** (with **SEAMWARE** FIWARE/EDC data-space components) and **H3 Smart Mesh** context enrichment for reusable city services.
- **Codogno (Italy) — Territory-to-City Agrifood Corridor Twin**: A medium-sized municipality in Lombardy's dairy and agrifood basin operating a bounded local digital twin and observatory led by **Politecnico di Milano (POLIMI)**, simulating producer flows, urban loading/access windows, intermodality, and corridor intelligence toward metropolitan demand nodes (Milano / Sogemi).

## Consortium

| Partner | Role | Country |
|---|---|---|
| **Ayuntamiento de Madrid — Dirección General de la Oficina Digital (DGOD)** | Pilot Lead & Public Authority | Spain (`ES`) |
| **Comune di Codogno** | Second Public Authority & Pilot Site | Italy (`IT`) |
| **capillar IT** | Technical Coordinator & Product Delivery Lead (NeWG, Smart Mesh, DPP continuity) | Spain (`ES`) |
| **SEAMWARE** | Data-Space Technology & Governance Provider (FIWARE / EDC) | Spain (`ES`) |
| **Mines Paris — PSL** | Scientific Partner, Methodology & Validation Lead | France (`FR`) |
| **Politecnico di Milano (POLIMI)** | Technical-Scientific Lead for Codogno Workstream | Italy (`IT`) |

## Pilot Coordination & Contacts

| Name | Role | Organisation | Contact |
|---|---|---|---|
| **Fernando Álvarez García** | Pilot Lead & Public Governance Lead (*Subdirector General de Transformación Digital, 5G / IoT*) | Ayuntamiento de Madrid — Dirección General de la Oficina Digital (DGOD) | `alvarezgf@madrid.es` |
| **Javier Esquillor** | Technical Coordinator & Managing Director | capillar IT | `javi@capillar.it` |
| **Andrés Julián** | Technical Coordinator, COO & Product Delivery Lead | capillar IT | `andres.j@capillar.it` |

## Repository Structure

- [`pilot.yaml`](pilot.yaml) — core metadata describing the NeWG+ pilot (name, partners, work strand, locations, focus areas, contacts), read by the LDT4SSC Knowledge Hub aggregator.
- [`updates/`](updates/) — structured updates on the pilot's journey: milestones, lessons learned, general progress, released assets, and events. See [`updates/README.md`](updates/README.md) for the schema and format:
  - [`2026-08-31-pilot-grant-agreement-signed-and-launch.md`](updates/2026-08-31-pilot-grant-agreement-signed-and-launch.md) (`milestone`)
  - [`2026-10-15-madrid-open-data-h3-smart-mesh-audit.md`](updates/2026-10-15-madrid-open-data-h3-smart-mesh-audit.md) (`general`)
  - [`2026-10-18-mercamadrid-and-municipal-areas-kickoff.md`](updates/2026-10-18-mercamadrid-and-municipal-areas-kickoff.md) (`event`)
- [`docs/`](docs/) — general project and architectural documentation ([`architecture.md`](docs/architecture.md), [`madrid-open-data-h3-smart-mesh.md`](docs/madrid-open-data-h3-smart-mesh.md), [`madrid-emt-and-open-data-catalog.md`](docs/madrid-emt-and-open-data-catalog.md)).
- [`assets/`](assets/) — references to shared artefacts and services contributed by NeWG+ to the LDT4SSC Assets and Services Repository and EU LDT Toolbox Marketplace.
- [`src/`](src/) — open-source software components, scripts, and integration tools shared by the pilot.
- [`data-models/`](data-models/) — NGSI-LD / Smart Data Models and semantic mappings used across the interconnected digital twins.

## Licensing

Code in this repository is licensed under the Apache License 2.0. Content and documentation are licensed under Creative Commons Attribution 4.0 International (CC BY 4.0) unless stated otherwise. See [`LICENSE`](LICENSE) for details.

## About LDT4SSC

LDT4SSC (Local Digital Twins for Smart and Sustainable Communities) is a project funded by the Digital Europe Programme under grant agreement number 101226211, developing an interconnected ecosystem of Local Digital Twins across Europe.

Learn more at the [LDT4SSC project website](https://ldt4ssc.eu/), the [LDT4SSC Knowledge Hub](https://knowledgehub.ldt4ssc.eu/), and the [NeWG+ Pilot Page](https://knowledgehub.ldt4ssc.eu/journey/pilots/round2/newg/).
