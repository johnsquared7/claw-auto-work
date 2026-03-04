# Discovery: NHS Analytics & Open Source BI Tools
**Date:** 2026-03-04 | **Source:** Autonomous Discovery Cycle

---

## 🔬 NHS-Specific Python & Data Tools

### 1. NHSDigital/data-analytics-services
**URL:** https://github.com/NHSDigital/data-analytics-services

The official NHS Digital Analytics team's open-source work. Contains:
- **codonPython** - Reduces barrier for new analysts at NHS Digital
- **Medicines text mining tool** - Python/PySpark for mining medicines data
- **Artificial Data Generator** - Generate anonymous synthetic NHS data in Databricks
- **DNAttend** - ML framework for predicting patient non-attendance
- **MultiNet** - CLI tool for multi-morbidity network analysis with community detection

**Why it's interesting:** Direct from NHS Digital - these are production-grade tools used internally.

---

### 2. SynPath - Synthetic Patient Pathway Generator
**URL:** https://github.com/nhsx/SynPath

Agent-based modeling to generate synthetic electronic health records in FHIR v4 format. Simulates patient journeys through hospitals, GPs, and other environments.

**Why it's interesting:** Can generate realistic synthetic patient data for testing analytics pipelines without touching real patient data (GDPR win).

---

### 3. Tuva Project
**URL:** https://github.com/tuva-health/tuva

Open source healthcare data model with:
- Core data model & data marts
- Data quality tests
- Terminology sets
- d forbt integration transformations
- Synthetic claims dataset for testing

**Why it's interesting:** Provides standardized healthcare data models that could map nicely to NHS data structures.

---

## 📊 Power BI Alternatives (Open Source)

### 4. Lightdash
**URL:** https://lightdash.com/

- Open source BI designed for data teams using dbt
- Self-hosted or cloud option
- Instant dashboards from dbt models
- **Best for:** Teams already using dbt for data transformation

### 5. Apache Superset
**URL:** https://superset.apache.org/

- Enterprise-ready open source BI
- Excellent for large datasets
- Rich visualization options
- **Best for:** Teams with experienced data engineers

### 6. Metabase
**URL:** https://www.metabase.com/

- Simple, user-friendly queries
- Great for non-technical stakeholders
- Embedded analytics option
- **Best for:** NHS analysts who need quick self-service without SQL

---

## ⚡ SQL Optimization for Healthcare Data

### 7. Table Partitioning for Healthcare (Medium)
**URL:** https://medium.com/@srikanth5b9/sql-server-performance-optimization-for-healthcare-systems-a-practical-guide-1a1df70a0c7b

Key techniques:
- **Partition elimination** can reduce data scanned by **90%+**
- Recent data (most accessed) isolated in smaller partitions
- Queries for last 30 days ignore years of historical data
- Index rebuilds on individual partitions (minutes vs hours)

**Why it matters:** If John's NHS queries hit large historical tables, partitioning could dramatically speed up monthly reports.

---

## 🎯 Relevance to John's NHS Workflow

| Need | Discovery |
|------|-----------|
| Automate NHS reports | SynPath for synthetic test data, Tuva for data modeling |
| Replace Power BI | Metabase (easiest), Lightdash (if using dbt), Superset (scale) |
| Speed up SQL queries | Table partitioning techniques from the healthcare SQL guide |
| Python for NHS data | codonPython from NHS Digital, NHS Python Community projects |

---

## 📁 Saved for Further Research

- NHSDigital intern projects: https://nhsx.github.io/nhsx-internship-projects/
- nhs_time_of_travel: Interactive mapping tool for health/social care decisions
- Forecasting repo: Various forecasting methods for healthcare

---

*Discovery completed 2026-03-04 12:00 UTC*
