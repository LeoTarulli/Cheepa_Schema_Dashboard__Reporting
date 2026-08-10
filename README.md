# Cheepá - Relational Database System & Dashboard

## 🗄️ Overview
This repository contains the complete relational data infrastructure designed for **Cheepá**. The project features a highly normalized SQL database schema structured to maintain strict data integrity, manage business operations cleanly, and track transactional metrics across sales, inventory, and marketing campaigns.

<img width="1089" height="627" alt="BoxPlot" src="https://github.com/LeoTarulli/Cheepa_schema/blob/main/Diagram.png"/>

---

## 📐 Relational Database Architecture

The backend system is designed around an optimized relational model that isolates master dimension data from transactional facts and handles temporal data variations, such as fluctuating product prices and costs.

### Key Components & Schema Breakdown

- **Core Transactional Tables (Facts & Details):**
  - `Orders`: Centralizes order metadata, linking transactions to specific employees, store locations, promotional ads, and customer categories.
  - `OrderDetails`: Maps individual items within an order, capturing exact quantities, transactional timestamps, and connecting directly to specific price and cost history records.

- **Inventory Tracking:**
  - `inventory` & `inventoryDetails`: Tracks real-time stock levels, quantities, and product distributions across various physical shop locations.

- **Historical Data Logging:**
  - `PriceHistory` & `CostHistory`: Log fluctuating unit prices and manufacturing costs by date. This architecture ensures historical sales records remain accurate even when a product's current price changes.

- **Master Dimensions:**
  - Dedicated master tables managing independent entities: `Products`, `employees`, `Categories`, `Contacto` (sales channels), `shops`, and `Ads`.

---

## 🛠️ Implementation & Technical Specifications

The complete Data Definition Language (DDL) script is written in standard SQL and is fully compatible with relational database management systems like MySQL. It establishes:
- Strict **Primary Keys (PK)** for unique record identification.
- **Foreign Keys (FK)** with cascading constraints to enforce data integrity and prevent orphaned records.
- Optimized data types (e.g., `TIMESTAMP`, `INT`, `FLOAT`, `VARCHAR`) tailored to business requirements.

You can view, copy, or execute the complete database creation script directly in the [`cheepa_schema.sql`](./cheepa_schema.sql) file.

## 📈 Business Intelligence & SQL Analytics

Beyond database architecture, this project contains advanced data analysis metrics designed to evaluate Cheepá's financial and operational health. The analytical environment uses a master `VIEW` as a staging layer to calculate:

- **Financial KPIs:** Aggregated Revenue, Costs, and Net Revenue trends analyzed monthly and per-order.
- **Advanced Benchmarking:** Query models comparing individual order values against overall historical averages using complex CTEs (`WITH` clauses) and `CROSS JOIN` methods.
- **Window Functions & Ranking:** Segmentations using `RANK()`, `DENSE_RANK()`, and `ROW_NUMBER() OVER (PARTITION BY...)` tracking purchase sequences, top customers by segment, and generating masked customer IDs (`CONCAT`).

📂 You can inspect the fully documented script in [`analytics_queries.sql`](./analytics_queries.sql).

# Cheepá - Business Performance Dashboard

## 📊 Overview
This repository contains the interactive business performance dashboard designed for **Cheepá**. Built using **Looker Studio**, this dashboard tracks and visualizes key sales metrics, revenue streams, costs, and customer acquisition trends over time to drive data-backed business decisions.

### 🔗 Live Dashboard
Link: https://datastudio.google.com/u/0/reporting/80c5aa99-1d63-4a8b-9783-011e4d84f2a4/page/Bk1sF

------
## 📷 Dashboard Preview

[![Cheepá Dashboard Preview](image_e14d5b.png)](https://datastudio.google.com/u/0/reporting/80c5aa99-1d63-4a8b-9783-011e4d84f2a4/page/Bk1sF)
*Note: Click on the image to open the dynamic version with active filters.*

## 🚀 Key Metrics Tracked

- **Financial Health:** Real-time visibility into **Total Income ($41.5M)**, **Gross Income ($29.37M)**, and **Total Costs ($12.1M)**, maintaining a strong **70.68% Gross Margin**.
- **Sales Breakdown:** Detailed tracking of products by revenue and volume (e.g., *Promo Clasico* leading with $12.36M generated across 1,353 units).
- **Customer Acquisition:** Historical analysis of total monthly customers and recurring vs. one-time buyer ratios.
- **Sales Channels:** Distribution analysis of revenue coming from Instagram, WhatsApp, and In-Person sales.

## 🛠️ Features & Interactivity

The dashboard includes dynamic controls to slice the data instantly by:
- **Month** 
- **Product**
- **Sales Category**
- **Point of Contact (POC)** / Sales Channel

## 🧰 Tech Stack
- **Data Visualization:** Looker Studio
- **Data Source:** Google Sheets and Google AppSheet
