<h2 align="center"><strong>GameZone Global Store - Commercial Performance &amp; Transaction Analytics</strong></h2>
<h3 align="left">Table of Content</h3>

1. [Business Background](#Business-Background)
2. [Analytical Objective](#analytical-objective)
3. [Dataset Details & Structures](#dataset-details-&-structure)
4. [Data Cleaning](#data-cleaning)
6. [Dashboard Tableau](#dashboard)
7. [Insight Key & Decision Making](#insight-key-decision-making)
8. [Potensi Strategi Bundling Produk](#potensi-strategi-bundling-produk)
9. [Kesimpulan Startegis](#kesimpulan-strategis)
10. [Struktur Folder & File](#struktur-folder--file)

<h3 align="left">Business Background</h3>

**GameZone** is a global gaming retail company offering a wide range of products for gaming needs, from core devices to supporting equipment. Its product portfolio includes:

- 🎮 Game Consoles
- 🖥️ Gaming Monitors
- 🎧 Gaming Accessories
- 💻 Gaming Laptops

With a diverse product portfolio and customers across multiple markets, GameZone generates transaction data that can be analyzed to understand **customer purchase behavior, product performance, market contribution, marketing channel effectiveness, and refund patterns**.

<h3 align="left">Analytical Objectives</h3>

| No | Objective |
|---|-----------|
| 1 | Analyze revenue trends and growth patterns |
| 2 | Identify key product to support revenue drivers |
| 3 | Evaluate marketing channel effectiveness |
| 4 | Identify key regions and assess revenue concentration |
| 5 | Evaluate refund by product |


<h3 align="left">Dataset Details &amp; Structure</h3>
The dataset comprises 17,088 customer transactions from 2018 to 2021, structured across two sheets (Region and Order).

**Dataset Structure**
| Orders                  | Region        |
|-------------------------|---------------|
| user_id                 | country_code  |
| order_id                | region        |
| purchase_ts             |               |
| ship_ts                 |               |
| refund_ts               |               |
| product_name            |               |
| product_id              |               |
| USD_price               |               |
| purchase_platform       |               |
| marketing_channel       |               |
| account_creation_method |               |
| country_code            |               |

<h3 align="left">Data Cleaning</h3>
Summarizes the data quality issues identified across the dataset:

| No. | Sheet  | Column                  | Data Quality Issue                          | Resolved? | Resolution |
|-----|--------|-------------------------|---------------------------------------------|-----------|------------|
| 1   | orders | purchase_ts             | Inconsistent date formats                   | Yes       | Standardized all date formats |
| 2   | orders | purchase_ts             | Missing date values (NULL)                  | No        | — |
| 3   | orders | product_name            | Inconsistent product names and categories   | Yes       | Standardized product names and categories |
| 4   | orders | usd_price               | $0 transaction values and NULL values       | No        | — |
| 5   | orders | marketing_channel       | Missing values (NULL)                       | Yes       | Replaced missing values with **"Unknown"** |
| 6   | orders | account_creation_method | NULL and "Unknown" values                   | Yes       | Standardized NULL values as **"Unknown"** |
| 7   | orders | country_code            | Missing country codes                       | Yes       | Filled missing country codes using a VLOOKUP from the **region** sheet |
| 8   | orders | All columns             | Duplicate records                           | Yes       | Removed **35 duplicate records** |
| 9   | region | region                  | Inconsistent country codes and NULL values  | Yes       | Standardized country codes and filled NULL values with the correct data |


<h3 align="left">Exploratory Data Analysis: Identifying Key Patterns by Objective</h3>

1️⃣ **Analyze revenue trends and growth patterns**

**Insight**

GameZone’s revenue showed strong growth through 2020, peaking at approximately $3.12M, followed by a sharp decline to around $0.4M in 2021.
