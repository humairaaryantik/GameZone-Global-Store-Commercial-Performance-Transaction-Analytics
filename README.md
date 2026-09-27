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
The dataset comprises 17,088 customer transactions from 2019 to 2021, structured across two sheets (Region and Order).

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

<p align="center">
  <img src="https://cdn.phototourl.com/member/2026-09-26-0488de9e-4111-4179-a734-af08705cc96c.png" width="400"/>
  <br>
  <em> Revenue Trends by Years</em>
</p>

**Insight**

<mark>GameZone’s revenue showed strong growth through 2020, peaking at approximately $4.05M, followed by a sharp decline to around $0.54M in 2021.</mark>

From 2019 to 2020, the COVID-19 pandemic led to lockdowns, school closures, and social distancing, limiting offline activities and increasing time spent at home. Gaming became one of the most accessible forms of home-based entertainment. **The significant revenue growth in 2020 may have been influenced by the pandemic, as increased time at home accelerated gaming engagement and digital purchases.** The World Economic Forum also reported that **Asia-Pacific was the largest gaming market by revenue, accounting for almost 50% of the global games market by value in 2020**, highlighting the strong global demand for gaming during the pandemic.

As restrictions gradually eased in 2021, consumers began returning to offline activities, potentially reducing the exceptional level of gaming demand observed in 2020.


2️⃣ **Identify key product to support revenue drivers**

<p align="center">
  <img src="https://cdn.phototourl.com/member/2026-09-27-6dbac813-ff05-46aa-ae2f-ab9d3ce55eeb.jpg" width="900"/>
  <br>
  <em> Product Revenue and Units Sold</em>
</p>

**Insight**

Top 4 Products by Revenue and Units Sold
| Product                         | Total Revenue | Units Sold | Product Category |
|---------------------------------|---------------|------------|------------------|
| 27in 4K Gaming Monitor          | $1.95M        | 4,688      | Gaming Monitor   |
| Nintendo Switch                 | $1.66M        | 10,386     | Game Console     |
| JBL Quantum 100 Gaming Headset  | $0.73M        | 4,296      | Gaming Accessories |
| Sony PlayStation 5              | $1.95M        | 977        | Game Console     |

<mark>Gaming hardware, particularly consoles and monitors, contributed the largest share of revenue among the top-performing products.</mark>

**Breakdown of Product Performance by Category**

- Gaming Monitor

| Product                    | Total Revenue | Units Sold | Average Price per Unit      |
|----------------------------|---------------|------------|-----------------------------|
| 27in 4K Gaming Monitor     | $1.95M        | 4,688      | $480                        |
| Acer Nitro V Laptop        | $0.07M        | 87         | $798                        |
| Lenovo IdeaPad 3           | $0.74M        | 669        | $1,198                      |

**Product performance is influenced by a combination of price, sales volume, and product value**. The 27in 4K Gaming Monitor achieved the highest revenue through its relatively affordable price and significantly higher sales volume, while the Lenovo IdeaPad Gaming 3 generated substantial revenue despite lower volume due to its higher price point. Interestingly, Lenovo sold significantly more units than the more affordable Acer Nitro V, suggesting that purchase decisions may depend not only on price, but also on factors such as product specifications, perceived value, and brand preference.


- Gaming Console

| Product                   | Total Revenue | Units Sold | Average Price per Unit |
|---------------------------|---------------|------------|-------------------------|
| Nintendo Switch           | $1.66M        | 10,386     | $168                    |
| Sony PlayStation 5 Bundle | $1.59M        | 977        | $1,726                  |

**Nintendo Switch generated nearly the same revenue as the Sony PlayStation 5 despite selling more than 10× the number of units**. This suggests that the Switch’s performance was primarily driven by high sales volume and a more affordable price point, while the significantly higher price of the PS5 may have limited its sales volume.

- Gaming Accecoris


| Product                         | Total Revenue | Units Sold | Average Price per Unit |
|---------------------------------|---------------|------------|-------------------------|
| JBL Quantum 100 Gaming Headset  | $0.10M        | 4,296      | $24                     |
| Dell Gaming Mouse               | $0.04M        | 719        | $50                     |
| Razer Pro Gaming Headset        | $884       | 7          | $120                       |

JBL Quantum 100 achieved the highest sales volume, supported by its more affordable price point. In contrast, the Razer Pro Gaming Headset had the highest price but the lowest sales volume, **suggesting that price may be one of the factors influencing purchase volume**.

3️⃣ **Evaluate marketing channel effectiveness**

<p align="center">
  <img src="https://cdn.phototourl.com/member/2026-09-27-ad5ad0a5-8bf0-47b6-9576-052b5ae2726c.jpg" width="500"/>
  <br>
  <em> Total Transactions by Marketing Channel</em>
</p>

**Insight**

**Direct dominated GameZone’s transactions, accounting for approximately 80% of total transactions**. Direct traffic generally represents customers accessing the store without a tracked referral source, such as typing the website URL directly, using bookmarks, or accessing the brand directly. **This high share may indicate strong customer familiarity or purchase intent with brand.**


4️⃣ **Identify key regions and assess revenue concentration**

Revenue by Top 10 Countries
| Country Code | Country Name | Revenue |
|--------------|--------------|--------:|
| US | United States | $2,947,679 |
| GB | United Kingdom | $474,498 |
| DE | Germany | $255,110 |
| CA | Canada | $232,100 |
| JP | Japan | $219,879 |
| AU | Australia | $187,830 |
| FR | France | $152,501 |
| BR | Brazil | $145,881 |
| ES | Spain | $105,733 |
| NL | Netherlands | $97,505 |

**The United States generated the highest revenue for GameZone at approximately $2.95M**. **This may be supported by the country’s large gaming ecosystem**; ESA reported that the U.S. gaming industry spans developers, publishers, hardware, and retail, while U.S. consumer spending on video games reached $60.4B in 2021.
