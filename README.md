# retail-banking-analytics
End-to-end SQL data pipeline and BI dashboard optimizing B2C term deposit conversions.
# Retail Banking Analytics: Optimizing Campaign Conversions & Macroeconomic Impact

## 📌 Executive Summary
In high-volume B2C outbound sales, operational friction occurs when agent time is misallocated toward low-yield demographics, resulting in diminishing returns and wasted marketing budget. 

This project involves the end-to-end development of a SQL-based data pipeline and Business Intelligence dashboard to analyze a retail bank's direct marketing campaigns (41,188 records). By engineering dimensional models and executing cohort analyses, this project identifies exact points of funnel drop-off and provides data-driven recommendations to reallocate agent outreach, significantly increasing the Lead-to-Conversion Rate.

## 🛠️ Technology Stack
* **Database Engine:** PostgreSQL 17
* **Query Design:** Advanced SQL (CTEs, Window Functions, Conditional Aggregations, Table Joins)
* **Data Visualization:** Metabase
* **Architecture:** Fact/Dimension Table Simulation, ETL Data Cleaning

---

## 📊 Strategic Business Insights

Through rigorous SQL exploration of the campaign data, three critical operational inefficiencies were identified:

### 1. The Demographic Yield Gap
* **Observation:** The `31-45` age bracket consumed the vast majority of agent resources (21,974 contact attempts) but yielded a poor conversion rate of **9.37%**. 
* **Insight:** Conversely, the `60+` demographic required only 915 contact attempts but delivered a massive **45.46%** conversion rate.
* **Recommendation:** Immediately cap cold-outreach volume to the 31-45 cohort and redirect marketing spend toward the highly liquid and receptive 60+ demographic.

### 2. The Contact Fatigue Threshold
* **Observation:** By grouping campaign contacts into distinct buckets, the data reveals a steep drop-off in subscription probability after multiple contact attempts.
* **Insight:** Dialing a prospect more than 3 times during a single campaign yields rapidly diminishing returns, burning valuable agent hours on dead leads.
* **Recommendation:** Implement a hard cap of 3 outbound dials per prospect per campaign cycle.

### 3. Occupational Sector Performance
* **Observation:** Using dimensional modeling to group discrete jobs into macro-sectors (`Corporate`, `Labor`, `Out of Workforce`), the non-working sector (students, retired) showed disproportionately high engagement.
* **Insight:** Traditional blue-collar and corporate outreach pipelines are highly saturated and resistant to standard daytime outbound calls.

---

## 🏗️ Data Architecture & Engineering

### Phase 1: Data Preparation & Cleaning
The raw `bank-additional-full.csv` dataset contained unstructured text entries and legacy tracking metrics.
* **Null Handling:** Executed auditing scripts to identify and standardize `'unknown'` string values across the `job`, `marital`, and `education` columns.
* **Data Type Enforcement:** Cast raw string identifiers into logical numeric values and structured text to ensure accurate aggregate mathematics.

### Phase 2: Relational Modeling (ETL)
To simulate an enterprise data warehouse environment, the flat analytical table was queried using dimensional modeling logic:
* Engineered Common Table Expressions (CTEs) to build temporary dimension tables (e.g., `dim_job_sector`).
* Executed `LEFT JOIN` operations to append these dimensional hierarchies back to the primary fact table, enabling segmented business reporting without altering the raw underlying data structure.

---

## 📈 Executive Dashboard Preview
*![Executive Dashboard](Metabase%20Dashboard.png*

---
*If you are a recruiter or hiring manager, please feel free to review the attached `.sql` files in this repository to examine the query structures, window functions, and aggregation logic used to generate these insights.*
