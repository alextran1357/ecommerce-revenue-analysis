# Ecommerce Revenue & Product Mix Analysis

## Executive Summary

This project analyzes multi-year ecommerce transaction data to understand revenue growth drivers, product mix trends, seasonality patterns, and pricing behavior. The dataset contains over **1.9 million order item records and more than 1 million orders**, providing a realistic simulation of production-scale ecommerce data.

The analysis focuses on identifying business risks and opportunities through structured data modeling, exploratory analysis, and dashboard reporting.

### Key Findings

- **Strong revenue growth:** Total revenue increased from approximately **$7.1M in 2022 to \$37.7M in 2025**, indicating rapid scaling of the business.
- **High product concentration:** Approximately **76% of total revenue is driven by a single product category (Gummies)**, creating significant dependency on one product line.
- **Strong seasonal demand:** Revenue is heavily concentrated in **Q4 (≈35% of yearly revenue)**, driven by holiday purchasing behavior.
- **Price changes across product lines:** Capsule prices dropped significantly between **Nov 2025 and Jan 2026**, while oil product prices gradually normalized from ~\$85 to ~\$55.
- **Promotional items in data:** Nearly **500k transactions show \$0 pricing**, largely representing promotional or free items (cards, influencer boxes, stickers).

### Business Implications

These findings highlight several potential operational risks and strategic opportunities:

- **Product concentration risk** if demand for the primary product category declines.
- **Seasonal revenue volatility** due to heavy reliance on holiday demand.
- **Potential margin pressure** resulting from price adjustments in key product categories.
- **Data quality considerations** when analyzing promotional products and $0 transactions.

This project demonstrates how analysts can transform raw ecommerce transaction data into actionable business insights through structured data cleaning, modeling, and exploratory analysis.

Future phases of this project will extend the analysis into **predictive modeling and forecasting**, transitioning the work from descriptive analytics toward data science.

## Dashboard Highlights

### Revenue Growth Over Time

Monthly revenue trends reveal strong growth beginning in late 2023 and accelerating through 2025, with clear seasonal spikes during the holiday months.

![Revenue Trend](visuals/RevenueByMonth.png)

---

### Revenue Contribution by Product Category

Product contribution analysis shows that **Gummies dominate revenue**, increasing their share over time while other product categories decline.

![Product Contribution](visuals/ContributionAnalysis.png)

---

### Power BI Dashboard Overview

The Power BI dashboard provides an interactive overview of revenue trends, product performance, price changes, and order volume across time.

![Power BI Dashboard](visuals/YoY.png)

---

# Dataset

The dataset represents ecommerce transaction activity across several years and includes orders, customers, and item-level purchase details.

### Tables

| Table | Rows |
|------|------|
| Customers | 326,673 |
| Orders | 1,018,641 |
| Order Items | 1,901,304 |

The data spans **2022–2026** and contains over **1.9 million item-level transactions**.

All sensitive fields were anonymized before publication.

---

# Data Engineering & Cleaning

The raw export contained several common issues seen in real production datasets.

## Data Structure Issues

- Data initially arrived in a **single flat structure**
- Several columns contained **nested JSON objects**
- Product attributes were embedded inside JSON fields
- Time columns contained duplicates

## Cleaning Steps

### Data extraction
- Parsed JSONL product fields using Python
- Converted nested structures into structured columns

### Data modeling
Split dataset into relational tables:

- `customers`
- `orders`
- `order_items`

### Power Query transformations

- Flattened nested JSON columns
- Standardized product type labels
- Removed duplicate customers
- Created normalized product categories

### Date modeling

- Built a dedicated calendar table
- Standardized time columns

### Data quality issues discovered

- ~2% of `createdAt` timestamps missing
- ~500k order items with **\$0 prices**
- ~389k records missing standardized product type
- Several promotional products incorrectly labeled

Many of the $0 price items were verified to be **expected promotional products** (cards, influencer boxes, stickers).

---

# Tools Used

### Data Processing
- Python (JSONL → CSV conversion)
- Excel Power Query (ETL transformations)

### Data Modeling
- Power Pivot
- Relational modeling
- DAX measures

### Visualization
- Excel Pivot Tables
- Power BI dashboards

### Large Dataset Handling
- DAX Studio used to export large Power Pivot tables

---

# Key Business Analyses

## Revenue Trend Analysis

Revenue grew substantially from **2023 through 2025**.

The dataset shows strong scaling of monthly revenue with particularly large increases beginning in late 2024.

Total revenue across all years reached approximately **$78.7M**.

Monthly analysis shows:

- consistent upward trend through 2025
- major spikes during holiday months
- sharp drop immediately after holiday periods

---

## Seasonality

Quarterly analysis shows heavy revenue concentration in **Q4 each year**.

Typical pattern:

- Q1–Q3 relatively stable
- Q4 accounts for **~35% of yearly revenue**

This indicates strong **holiday-driven demand cycles**.

---

## Product Mix Analysis

Revenue is extremely concentrated in one product category.

### Product revenue share

| Product | Revenue Share |
|--------|---------------|
| Gummies | ~76% |
| Oils | ~10% |
| Capsules | ~2–8% |
| Oil for Pets | ~1–4% |
| Topicals | ~2–9% |

Over time, gummies increased from roughly **60–70% of revenue to over 85% in some months**.

This indicates growing **product concentration risk**.

---

## Revenue Contribution Trends

Contribution analysis revealed:

- Gummies steadily increasing market share
- Capsules and oils gradually losing share
- Minor products declining to negligible revenue

This suggests the company is increasingly dependent on a single product category.

---

## Pricing Trends

Product pricing analysis showed notable shifts across several product types.

### Oils
- Started around **\$85 average price**
- Gradually normalized to roughly **\$55**

### Capsules
- Major price drop between **Nov 2025 → Jan 2026**
- From ~\$60 to ~\$44

These price changes may indicate:

- promotional campaigns
- competitive price pressure
- margin adjustments

---

## Order Volume Trends

Order count analysis showed major volume spikes in **November and December**, reinforcing the strong seasonal demand pattern.

Monthly order counts exceeded **70k orders during peak holiday months**, indicating significant operational scaling during Q4.

---

# Key Business Risks Identified

## Product Concentration Risk

With roughly **76% of revenue coming from gummies**, the company is highly exposed to demand shifts in a single product category.

---

## Seasonal Revenue Volatility

Heavy dependence on Q4 revenue creates operational risk if holiday demand weakens.

---

## Price Compression

Large price drops in some categories may indicate margin pressure or competitive pricing pressure.

---

## Data Quality Risk

Promotional items and inconsistent product labeling can distort revenue analysis if not properly handled.

---

# Dashboard Overview

The Power BI dashboard explores several key analytical areas:

- Revenue growth trends
- Year-over-year revenue changes
- Product-level revenue trends
- Product pricing changes
- Order volume trends

Example dashboard views include:

- Monthly revenue breakdown
- Product contribution analysis
- Average product price by category
- Order count by product type

---

# Future Work (Data Science Phase)

This project will be extended with predictive modeling and deeper behavioral analysis.

Planned extensions include:

## Revenue Forecasting

- SARIMA / Prophet time-series forecasting
- Holiday demand modeling

## Customer Analysis

- Customer cohort analysis
- Repeat purchase modeling
- Customer lifetime value estimation

## Product Demand Modeling

- Price elasticity estimation
- Product substitution analysis

## Risk Simulation

- Monte Carlo simulation of seasonal revenue variability

These additions will transition the project from **descriptive analytics → predictive analytics**.

---

# Key Skills Demonstrated

- Data cleaning & transformation
- Handling nested JSON data
- Relational data modeling
- Large dataset handling
- Business-focused exploratory analysis
- Dashboard design
- Risk-focused business interpretation
