

# NYC Taxi Data Engineering Project with Microsoft Fabric

An end-to-end data engineering and analytics project built with Microsoft Fabric and NYC Yellow Taxi trip data. The project ingests and transforms trip records, enriches them with taxi zone information, tracks processing metadata, and presents the results in a Power BI report.

> **Project status:** The pipeline runs successfully and refreshes the data when executed. A Power BI report has also been created. This repository documents the project and can include screenshots, SQL scripts, and an exported Power BI file if available.

---

## Project Overview

This project demonstrates a data workflow that:

1. Loads monthly taxi trip data and a taxi zone lookup file into Microsoft Fabric.
2. Uses Dataflow Gen2 to clean, type, and enrich the data.
3. Processes data through staging and presentation tables.
4. Uses SQL procedures to clean records and write processing metadata.
5. Presents trip, passenger, payment, and revenue information in Power BI.

---

## Project Screenshots

### Microsoft Fabric Workspace and Item Lineage

This screenshot shows the Fabric items used in the project and how the warehouse, lakehouse, dataflows, pipelines, semantic model, and report are connected.

<img width="1417" height="655" alt="Screenshot 2026-11-12 160936" src="https://github.com/user-attachments/assets/d81581d5-0ea3-47aa-9343-585f92a4cb4d" />


---

### Dataflow Gen2 Transformation

This screenshot shows the Dataflow Gen2 transformation steps, including the trip data and taxi zone lookup merge, column type changes, and transformed output.

**ADD IMAGE HERE — Dataflow Gen2 screenshot**

---

### Power BI Dashboard

This screenshot shows the report page with trip and passenger KPIs, revenue, payment method comparisons, a date range filter, and vendor and payment filters.

<img width="1531" height="732" alt="Screenshot 2026-11-12 160702" src="https://github.com/user-attachments/assets/885c6a63-a051-4bf0-8e49-613e6f1eff50" />


---

## Dataset
https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page

- **Data:** NYC Yellow Taxi trip records and taxi zone lookup reference data.
- **Trip data format:** Monthly Parquet files.
- **Lookup data:** CSV file containing taxi zone and borough information.
- **Fields used in the presentation table:** Vendor, pickup and drop-off dates, pickup and drop-off boroughs and zones, payment method, passenger count, trip distance, and total amount.
- **Raw data:** Not included in this repository because the source files are large.

---

## Technology Stack

- Microsoft Fabric
- Fabric Lakehouse and Warehouse
- Dataflow Gen2 / Power Query
- Fabric Data Pipelines
- SQL stored procedures
- Metadata logging
- Power BI semantic model and report
- Parquet and CSV

---

## Architecture

```mermaid
flowchart LR
    A[Monthly Yellow Taxi Parquet files] --> B[Fabric Lakehouse]
    L[Taxi zone lookup CSV] --> B
    B --> C[Dataflow Gen2 transformations]
    C --> D[Staging table: stg.nyctaxi_yellow]
    D --> E[Staging date-range cleanup]
    E --> F[Presentation table: dbo.nyctaxi_yellow]
    D --> G[Staging processing metadata]
    F --> H[Power BI semantic model]
    H --> I[NYC Taxi Power BI report]
    F --> J[Presentation processing metadata]
