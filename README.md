#  London Public Transport Demand Analysis (SQL Case Study)

##  Project Overview

This project analyzes monthly public transport journey data from **Transport for London (TfL)** to evaluate demand patterns across transport modes and over time.

The objective was to move beyond simple querying and approach the dataset from a **data analyst perspective**:

* Define meaningful KPIs
* Aggregate data at the right level
* Identify structural demand shifts
* Translate numbers into operational insight

All analysis was conducted using SQL in Snowflake.

---

#  Dataset Description

**Database:** `TFL`
**Table:** `JOURNEYS`

### Columns:

| Column            | Description                  | Data Type |
| ----------------- | ---------------------------- | --------- |
| MONTH             | Month number (1 = January)   | INTEGER   |
| YEAR              | Reporting year               | INTEGER   |
| DAYS              | Number of days in month      | INTEGER   |
| REPORT_DATE       | Date reported                | DATE      |
| JOURNEY_TYPE      | Mode of transport            | VARCHAR   |
| JOURNEYS_MILLIONS | Total journeys (in millions) | FLOAT     |

---

##  Dataset Scope

The dataset contains approximately **936 monthly records**, structured across:

* 13 years (2010–2022)
* 12 months per year
* 6 transport types

**Structure calculation:**
13 × 12 × 6 = **936 rows**

This granularity enables:

* Time-series trend analysis
* Mode-level performance comparison
* Year-over-Year demand evaluation
* Shock detection (e.g., disruption impact)



#  Analytical Thought Process

Before writing SQL queries, I defined:

### 1️ What defines popularity?

→ **Total Journey Volume (SUM of JOURNEYS_MILLIONS)**

### 2️ What aggregation level provides clarity?

→ Monthly data aggregated to yearly totals

### 3️ What indicates structural disruption?

→ Significant Year-over-Year declines

### 4️ How do I measure dependency risk?

→ Mode-wise share of total journeys

The dataset reports journeys in millions, so aggregation functions became the primary driver of analysis.

---

# 📈 Key KPIs Used

| KPI                           | Definition                 | Business Purpose                    |
| ----------------------------- | -------------------------- | ----------------------------------- |
| **Total Journeys (Millions)** | SUM(JOURNEYS_MILLIONS)     | Measures overall demand             |
| **Mode Share %**              | Mode total ÷ Overall total | Identifies dependency concentration |
| **Yearly Total Journeys**     | Aggregated by YEAR         | Detects trend shifts                |
| **Lowest Demand Year**        | Min yearly total           | Identifies structural shock         |

---

# 🔍 Analysis & Key Findings

## 1️⃣ Overall Demand by Transport Type

### KPI:

Total Journeys (Millions)

| Transport Type        | Total Journeys (Millions) |
| --------------------- | ------------------------- |
| **Bus**               | **24,905.19M**            |
| **Underground & DLR** | **15,020.47M**            |
| Overground            | 1,666.85M                 |
| TfL Rail              | 411.31M                   |
| Tram                  | 314.69M                   |
| Emirates Airline      | 14.58M                    |

### Insights:

* **Bus services account for the highest demand (~25B journeys)**.
* Underground & DLR contribute significantly but remain ~40% lower than buses.
* Emirates Airline contributes less than **0.03% of total journeys**, indicating non-core usage.

### Business Interpretation:

Demand is heavily concentrated in bus and underground systems. Resource allocation, operational planning, and infrastructure investment should prioritize these modes.

---

## 2️ Emirates Airline Performance Evaluation

### KPI:

Monthly Journey Volume

Despite being included in the transport portfolio, Emirates Airline shows negligible contribution compared to core services.

### Insight:

This service likely serves tourism or limited corridor usage rather than commuter demand.

### Business Implication:

Performance evaluation for such services should focus on strategic value rather than volume efficiency.

---

## 3️ Underground Demand Shock Analysis

### KPI:

Yearly Total Underground Journeys

| Year     | Total Journeys (Millions) |
| -------- | ------------------------- |
| **2020** | **310.18M**               |
| 2021     | 748.45M                   |
| 2022     | 1,064.86M                 |
| 2010     | 1,096.15M                 |
| 2011     | 1,156.65M                 |

### Insights:

* 2020 recorded the lowest Underground usage.
* Demand dropped sharply compared to historical norms.
* Recovery began post-2020 but did not immediately return to peak levels.

### Analytical Conclusion:

Underground systems are highly sensitive to macro disruptions. This indicates higher volatility risk compared to bus services.

---

#  SQL Skills Demonstrated

* Aggregation using `SUM()`
* Filtering using `WHERE` and `LIKE`
* Grouping with `GROUP BY`
* Sorting using `ORDER BY`
* Limiting results using `LIMIT`
* Translating numeric output into strategic insight

---

#  Business Takeaways

* Transport demand is highly concentrated in two modes: Bus and Underground.
* Non-core services contribute marginally to total system volume.
* Underground services show higher volatility under external shocks.
* Monthly granularity enables strong time-series aggregation for decision support.

This project demonstrates the ability to:

* Understand dataset structure
* Define relevant KPIs
* Extract meaningful trends
* Interpret numerical results in a business context

---

#  Tech Stack

* SQL
* Snowflake
* DataLab

---

##  Author

Aditi Kadam
Master’s in Business Analytics

---

