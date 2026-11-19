# Madrid Open Data Catalog Analysis — H3 Smart Mesh & NeWG+ Integration

**Project:** NeWG+ Madrid (LDT4SSC Work Strand 1 / Mercamadrid & Municipal Organizational Units)  
**Source Portal:** [datos.madrid.es](https://datos.madrid.es/dataset) (Ayuntamiento de Madrid CKAN API & `informo.madrid.es` / `mc30.es` Live Feeds)  
**Date:** October 15, 2026  
**Objective:** Identify, verify, and map live and structural datasets from Madrid's Open Data portal covering **street closures (`calles cortadas`)**, **traffic speed & intensity (`velocidad e intensidad`)**, and **complementary urban logistics layers** to power the **H3 Spatial Smart Mesh** in NeWG+.

---

## Executive Summary

A live audit of the Madrid Open Data CKAN API (`https://datos.madrid.es/api/3/action/package_search`) across 131 catalog entries and direct inspection of the live XML/KML streams from `informo.madrid.es` and `mc30.es` confirm that **Madrid provides all foundational real-time and structural data required to build the H3 Smart Mesh without deploying dedicated hardware sensors**:

1. **Real-Time Street Closures & Roadworks:** Available every **5 minutes** via XML (`incid_aytomadrid.xml`) and KML (`PTINFO.kml`), plus dedicated M-30 ring-road feeds (`incidencias.xml`, `ObrasPlanificados.xml`). Each record provides exact WGS84 (`latitud`, `longitud`) and UTM (`utm_x`, `utm_y`) coordinates, start/end timestamps (`fh_inicio`, `fh_final`), and boolean flags (`es_obras`, `es_accidente`, `es_contaminacion`).
2. **Traffic Speed, Load & Level of Service:** Available every **5 minutes** across **4,000+ measurement points** (`pm.xml`) combined with M-30 live travel-time/speed estimations (`EstimacionesTrafico.xml`) and the structural **Annual Average Daily Speed by Street Segment** (`300340-0-trafico-velocidad`).
3. **Urban Logistics & Last-Mile Capacity (DUM 360):** Madrid publishes both the **geolocated inventory of Loading/Unloading bays (`208072-0-carga-descarga`)** and the **historical DUM 360 parking ticket logs (`300747-0-tiques-carga-descarga`)**, enabling predictive bay-occupancy modeling per H3 cell around **Mercado de Maravillas** (and extensible via `200967-0-mercados` across Madrid's 46 Municipal Markets).
4. **Environmental, ZBE & Public Health Layers:** Live hourly Air Quality (`212531-0-calidad-aire-tiempo-real`), ZBE OCR enforcement cameras (`300654-0`), EV fast-charging stations (`208979-0`), Mercamadrid wholesale volumes (`300357-0`), and Madrid Salud food-safety inspections (`300382-0`).

---

## 1. Street Closures, Roadworks & Public Way Incidences (`Calles Cortadas`)

These datasets enable the H3 engine to dynamically **block hex edges** or apply **time-bounded routing penalties** when streets, lanes, or tunnels are closed due to roadworks, accidents, or municipal events.

### 1.1 Primary Datasets & Live Endpoints

| Dataset ID & Catalog Link | Update Frequency & Formats | Live Endpoint / Resource URL | H3 Mesh Role |
| :--- | :--- | :--- | :--- |
| **[`202062-0-trafico-incidencias-viapublica`](https://datos.madrid.es/dataset/202062-0-trafico-incidencias-viapublica)**<br>*Tráfico. Incidencias en vía pública* | **Real-Time (every 5 min)**<br>`XML` | [`https://informo.madrid.es/informo/tmadrid/incid_aytomadrid.xml`](https://informo.madrid.es/informo/tmadrid/incid_aytomadrid.xml) | **Primary closure & incidence feed** for surface streets and municipal tunnels (active + scheduled within 24h). |
| **[`208252-0-incidencias-viapublica-mapa`](https://datos.madrid.es/dataset/208252-0-incidencias-viapublica-mapa)**<br>*Tráfico. Incidencias en vía pública. Mapa* | **Real-Time (every 5 min)**<br>`KML` | [`https://informo.madrid.es/informo/tmadrid/PTINFO.kml`](https://informo.madrid.es/informo/tmadrid/PTINFO.kml) | Vector geometries of affected street segments for direct spatial `polyfill` across H3 cells. |
| **[`212171-0-trafico-calle30-incidencias`](https://datos.madrid.es/dataset/212171-0-trafico-calle30-incidencias)**<br>*Tráfico. Calle 30. Incidencias* | **Real-Time**<br>`XML` | [`https://mc30.es/xml-data/incidencias.xml`](https://mc30.es/xml-data/incidencias.xml) | **Critical for Mercamadrid outbound corridors** (Nudo Sur / M-30 ring road active closures and accidents). |
| **[`212422-0-trafico-calle30-planificados`](https://datos.madrid.es/dataset/212422-0-trafico-calle30-planificados)**<br>*Tráfico. Calle 30. Trabajos planificados en tiempo real* | **Real-Time**<br>`XML` | [`https://mc30.es/xml-data/ObrasPlanificados.xml`](https://mc30.es/xml-data/ObrasPlanificados.xml) | Scheduled night/day maintenance closures on M-30 tunnels and ramps. |
| **[`202974-0-trafico-semaforos`](https://datos.madrid.es/dataset/202974-0-trafico-semaforos)**<br>*Tráfico. Semáforos apagados o en destellos* | **Real-Time (every 5 min)**<br>`XML` | [`https://informo.madrid.es/informo/tmadrid/EstadosCruces.xml`](https://informo.madrid.es/informo/tmadrid/EstadosCruces.xml) | Detects unpowered or flashing traffic lights causing intersection friction (cross-referenced with static inventory [`300275-0-cruces-semaforizados`](https://datos.madrid.es/dataset/300275-0-cruces-semaforizados)). |
| **[`300531-0-incidencias-viapublica-historico`](https://datos.madrid.es/dataset/300531-0-incidencias-viapublica-historico)**<br>*Tráfico. Incidencias en vía pública. Histórico* | **Historical Archive**<br>`ZIP / XML` | [Catalog Page](https://datos.madrid.es/dataset/300531-0-incidencias-viapublica-historico) | Historical log of street closures to train predictive disruption profiles by district and season. |

---

## 2. Traffic Speed, Intensity & Congestion (`Velocidad e Intensidad`)

### 2.1 Primary Speed & Traffic Datasets

| Dataset ID & Catalog Link | Update Frequency & Formats | Live Endpoint / Resource URL | H3 Mesh Role |
| :--- | :--- | :--- | :--- |
| **[`202087-0-trafico-intensidad`](https://datos.madrid.es/dataset/202087-0-trafico-intensidad)**<br>*Tráfico. Datos del tráfico en tiempo real* | **Real-Time (every 5 min)**<br>`XML` | [`https://informo.madrid.es/informo/tmadrid/pm.xml`](https://informo.madrid.es/informo/tmadrid/pm.xml) | **Core real-time telemetry** across 4,000+ loop detectors: `<intensidad>`, `<ocupacion>`, `<carga>`, `<nivelServicio>`, `<velocidad>`, `<st_x>`, `<st_y>`. |
| **[`300340-0-trafico-velocidad`](https://datos.madrid.es/dataset/300340-0-trafico-velocidad)**<br>*Tráfico. Velocidad media diaria anual por tramos* | **Structural Baseline**<br>`KML`, `XLSX`, `ZIP` | [Download KML](https://datos.madrid.es/dataset/300340-0-trafico-velocidad/resource/300340-2-trafico-velocidad-kml/download/300340-2-trafico-velocidad-kml) | Provides the **structural baseline speed (km/h) per street segment** to calibrate H3 cells under free-flow vs. congested states. |
| **[`212132-0-trafico-calle30-estimaciones`](https://datos.madrid.es/dataset/212132-0-trafico-calle30-estimaciones)**<br>*Tráfico. Calle 30. Estimaciones de tiempos de recorrido* | **Real-Time (every 5 min)**<br>`XML` | [`https://mc30.es/xml-data/EstimacionesTrafico.xml`](https://mc30.es/xml-data/EstimacionesTrafico.xml) | Live travel times and speeds between M-30 entries and exits (Mercamadrid ↔ Mercado de Maravillas trunk route). |
| **[`212117-0-trafico-calle30-general`](https://datos.madrid.es/dataset/212117-0-trafico-calle30-general)**<br>*Tráfico. Calle 30. Datos generales de tráfico* | **Real-Time (every 5 min)**<br>`XML` | [`https://mc30.es/xml-data/DatosTrafico.xml`](https://mc30.es/xml-data/DatosTrafico.xml) | Live vehicle counts, speeds, and congestion status along M-30 sections. |
| **[`208223-0-trafico-intensidad-tramas`](https://datos.madrid.es/dataset/208223-0-trafico-intensidad-tramas)**<br>*Tráfico. Mapa de tramas de intensidad del tráfico* | **Real-Time (every 5 min)**<br>`KML` | [`https://informo.madrid.es/informo/tmadrid/INTENSIDADES.kml`](https://informo.madrid.es/informo/tmadrid/INTENSIDADES.kml) | Live color-coded traffic corridors and polygons (Fluid, Slow, Retention, Closed) for H3 visual overlay and segment interpolation. |

---

## 3. Domain-Specific Layers across Municipal Areas

- **Urban Freight Distribution & Loading Bays (`Movilidad & DUM 360`)**:
  - [`208072-0-carga-descarga`](https://datos.madrid.es/dataset/208072-0-carga-descarga) — Geolocated inventory of loading/unloading bays (`CSV`, `XLSX`, `GEO`).
  - [`300747-0-tiques-carga-descarga`](https://datos.madrid.es/dataset/300747-0-tiques-carga-descarga) — Historical DUM 360 parking ticket logs (`CSV`) for hourly bay-saturation probability curves per H3 cell.
- **Wholesale & Retail Commercial Nodes (`Comercio, Mercamadrid & Mercados`)**:
  - [`200967-0-mercados`](https://datos.madrid.es/dataset/200967-0-mercados) — Geolocation of Madrid's 46 Municipal Markets.
  - [`210006-0-mercados-municipales-puestos`](https://datos.madrid.es/dataset/210006-0-mercados-municipales-puestos) — Census of stalls (`puestos`) inside each municipal market.
  - [`300358-0-mercamadrid-empresas-ubicacion`](https://datos.madrid.es/dataset/300358-0-mercamadrid-empresas-ubicacion) & [`300357-0-mercamadrid-volumen-precio`](https://datos.madrid.es/dataset/300357-0-mercamadrid-volumen-precio) — Mercamadrid wholesale operators, volumes, and prices.
- **Decarbonization, Air Quality & Low Emission Zones (`Medio Ambiente & Madrid 360`)**:
  - [`212531-0-calidad-aire-tiempo-real`](https://datos.madrid.es/dataset/212531-0-calidad-aire-tiempo-real) — Real-time hourly Air Quality API.
  - [`300654-0-circulacion-camaras-trafico`](https://datos.madrid.es/dataset/300654-0-circulacion-camaras-trafico) — ZBE automated OCR enforcement cameras.
  - [`208979-0-puntos-recarga-historico`](https://datos.madrid.es/dataset/208979-0-puntos-recarga-historico) — Public EV fast-charging stations.
- **Public Health & Administrative Boundaries (`Madrid Salud` & `Oficina Digital`)**:
  - [`300382-0-inspecciones-salud-publica`](https://datos.madrid.es/dataset/300382-0-inspecciones-salud-publica) & [`211931-0-inspecciones-alimentacion`](https://datos.madrid.es/dataset/211931-0-inspecciones-alimentacion) — Municipal food-safety and transport inspection records.
  - [`300497-0-distritos-municipales-madrid`](https://datos.madrid.es/dataset/300497-0-distritos-municipales-madrid) & [`300496-0-barrios-madrid`](https://datos.madrid.es/dataset/300496-0-barrios-madrid) — Official boundaries of Madrid's 21 Districts and 131 Neighborhoods (`Barrios`).
