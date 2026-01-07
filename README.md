![System Architecture](assets/Flight-Ops-Analytics-Pipeline.drawio.svg)
# ✈️ Global Flight Operations Monitoring Dashboard  
*Using OpenSky Network Data*

---

## 1. Executive Summary

This project delivers an end-to-end flight operations analytics solution built on real-time aviation data from the OpenSky Network API. The objective was to transform raw aircraft state vectors into actionable operational insights that highlight global flight activity, movement efficiency, and ground congestion patterns.

Using a modern data stack—Python for ingestion and transformation, a Medallion Architecture (Bronze, Silver, Gold) for data modeling, Apache Airflow for orchestration, Snowflake for analytics, and Power BI for visualization—the dashboard reveals meaningful trends such as traffic concentration by country, aircraft velocity efficiency, and regions experiencing operational bottlenecks on the ground.

The analysis confirms expected real-world behavior (e.g., the United States leading in total flight volume) while also surfacing less obvious insights, such as countries with high traffic but reduced average velocities, indicating potential congestion or airspace constraints.

---

## 2. Business Problem

Global flight operations involve thousands of aircraft operating simultaneously across different regions. For aviation stakeholders—such as airport operators, regulators, logistics providers, and analysts—understanding **where flights are concentrated**, **how efficiently aircraft are moving**, and **where congestion is occurring** is critical for:

- Identifying operational bottlenecks  
- Improving air traffic efficiency  
- Supporting capacity planning and resource allocation  
- Monitoring regional aviation performance  

However, raw aviation telemetry data is complex, high-volume, and not immediately analysis-ready.

**This project addresses the problem of transforming raw flight telemetry into clear, decision-ready operational insights.**

---

## 3. Methodology

### Data Ingestion & Processing
- Extracted live aircraft state vectors from the **OpenSky Network API**
- Parsed and standardized raw JSON responses using Python
- Handled missing values, inconsistent fields, and timestamp normalization

### Data Architecture
Implemented a **Medallion Architecture**:
- **Bronze Layer:** Raw OpenSky API responses (unaltered)
- **Silver Layer:** Cleaned, structured flight records with standardized columns
- **Gold Layer:** Aggregated KPIs such as total flights, average velocity, and grounded aircraft by country

### Orchestration
- Used **Apache Airflow** to orchestrate:
  - API extraction
  - Transformations across Bronze → Silver → Gold
  - Loading aggregated data into Snowflake

### Analytics & Visualization
- Loaded Gold-layer tables into **Snowflake**
- Ran analytical SQL queries to derive KPIs
- Built an interactive **Power BI dashboard** for flight operations monitoring

---

## 4. Tools & Skills Used

### 🐍 Python
- Pandas (data cleaning and transformations)
- NumPy (numerical operations)
- Writing reusable functions
- API data extraction
- Basic statistical analysis
- Building a data “product funnel” (raw → clean → aggregated)

---

### 🗄️ SQL (Snowflake)
- Common Table Expressions (CTEs)
- Aggregate functions (`SUM`, `AVG`, `COUNT`)
- `CASE` statements
- Filtering and grouping
- Analytical KPI generation

---

### 🔄 Apache Airflow
- DAG design and scheduling
- Task dependencies
- PythonOperator usage
- End-to-end pipeline orchestration
- Error handling and retries

---

### 📊 Power BI
- Data modeling
- DAX measures
- Calculated columns
- ETL within Power BI
- KPI cards and comparative visualizations
- Dashboard design and storytelling

---

### 🧱 Data Engineering Concepts
- Medallion Architecture
- Separation of raw and analytics-ready data
- Pipeline reliability and reproducibility
- Scalable data modeling for analytics

---

## 5. Results & Key Insights

### Key Findings

- **The United States leads global flight activity**, reflecting its role as the world’s largest aviation hub.
- Countries with **high total flights but lower average velocities** indicate potential airspace congestion or traffic density.
- Regions with a **high proportion of grounded aircraft** suggest airport capacity constraints or operational delays.
- Countries with **moderate traffic but higher average velocities** demonstrate more efficient airspace utilization.

---

## 6. Recommendations

1. **Monitor High-Traffic, Low-Velocity Regions**  
   These areas may benefit from improved air traffic flow management or infrastructure investment.

2. **Track Grounded Aircraft Ratios as a Congestion Signal**  
   A rising percentage of grounded aircraft can act as an early indicator of operational bottlenecks.

3. **Use Velocity Metrics for Efficiency Benchmarking**  
   Comparing average velocity across regions helps identify best-performing airspaces and operational best practices.

4. **Extend the Model with Time-Based Trends**  
   Adding hourly or daily trend analysis could support peak-time congestion forecasting.

---

## 7. Conclusion

This project demonstrates how raw aviation telemetry can be transformed into meaningful operational intelligence using modern data engineering and analytics practices. It showcases both technical execution and business-focused insight generation, bridging the gap between complex data and real-world decision-making.
