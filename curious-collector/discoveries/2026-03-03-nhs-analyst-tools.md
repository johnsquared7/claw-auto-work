# Discovery: NHS Analyst Workflow Tools
**Date:** 2026-03-03
**Source:** Autonomous Discovery Cycle

---

## 🔥 Polars - The Fast DataFrame Library

**What:** High-performance DataFrame library written in Rust with Python bindings  
**Why interesting:** 10x faster than pandas for large datasets, lazy evaluation, better memory efficiency  
**Relevance:** NHS data often involves large patient datasets - Polars could speed up transforms significantly  
**GitHub:** github.com/pola-rs/polars

> "Polars is a fast DataFrame library written in Rust with Python bindings, offering significant performance gains over pandas for large datasets."

---

## 🔥 Apache Superset - Open Source BI Alternative

**What:** Open-source business intelligence and data exploration platform  
**Why interesting:** Free, self-hostable, SQL Lab for querying, interactive dashboards  
**Relevance:** Could replace Power BI for NHS dashboards - works with PostgreSQL, supports embedding  
**Website:** superset.apache.org

> "Self-serve analytics: interactive dashboards, chart builder, SQL Lab, dataset management. Extensive database compatibility."

---

## 🔥 Metabase - No-Code Data Tool

**What:** Easy-to-use open-source BI with no-code query builder  
**Why interesting:** Free tier, simple setup, question builder for non-technical users  
**Relevance:** NHS staff could build their own reports without SQL knowledge  
**Website:** metabase.com

> "No-code tool for business analytics - open-source version free, paid plans cheap to get started."

---

## 🔥ydata-profiling (formerly pandas-profiling)

**What:** Automated EDA (Exploratory Data Analysis) reports  
**Why interesting:** Generates comprehensive HTML reports with statistics, correlations, missing values in seconds  
**Relevance:** Quickly understand new NHS datasets - saves hours of initial exploration  
**GitHub:** github.com/ydataai/ydata-profiling

---

## 🔥 SQL Optimization Techniques for Data Warehouses

**Key findings from research:**

| Technique | Benefit |
|-----------|---------|
| Partition pruning | Skip irrelevant data chunks |
| Materialized views | Pre-compute expensive joins |
| Bitmap join indexes | Order-of-magnitude speedup for fact/dimension joins |
| Selective columns | Reduce data scanned = faster queries |
| Sort keys | Optimize range queries |

**Relevance:** NHS data warehouses benefit from materialized views for common report queries

---

## 📌 Saved for Later

- **Dask** - Parallel pandas for out-of-memory datasets
- **Vaex** - Lazy DataFrames for billion-row datasets  
- **Looker/Tableau** - Enterprise BI (costly but powerful)
- **Qlik** - Associative model for unexpected data relationships

---

*Quality check: These are specific tools with clear NHS workflow relevance - not generic AI news.*
