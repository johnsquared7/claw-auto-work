# Discovery — 2026-03-06

*Autonomous discovery cycle for John's NHS analyst workflow*

---

## 1. Pandera — Schema Validation for Pandas DataFrames

**URL:** https://pandera.readthedocs.io/

**What it is:** Statistical data validation library that brings type-hinting and schema validation to pandas DataFrames.

**Why it's interesting for John:**
- Define schemas with expected data types, value ranges, and statistical properties
- Validate NHS data imports before they corrupt downstream reports
- Catches data quality issues early in ETL pipelines
- Integrates with pandas — minimal code changes
- Supports hypothesis testing within schema definitions

**NHS Use Case:** Validate incoming patient data CSVs against expected schemas before processing. Catch column type mismatches, missing values, and out-of-range data automatically.

**Relevance:** High — addresses data quality concerns in NHS reporting

---

## 2. Sweetviz — Automated EDA with Dataset Comparison

**URL:** https://github.com/fbdesignpro/sweetviz

**What it is:** Automated EDA library that creates HTML reports with detailed visualizations and comparisons between datasets.

**Why it's interesting for John:**
- Generate comprehensive EDA reports in seconds
- Compare training vs test sets (or before vs after data transformations)
- Target analysis shows how features relate to target variable
- Association analysis reveals correlations across all features
- Perfect for NHS quarterly report comparisons

**NHS Use Case:** Generate quick HTML reports comparing this month's vs last month's data quality. Share with stakeholders without building dashboards.

**Relevance:** High — speeds up exploratory analysis

---

## 3. Vaex — Out-of-Core DataFrames for Billions of Rows

**URL:** https://vaex.io/

**What it is:** High-performance Python library for lazy, out-of-core DataFrames. Handle datasets larger than RAM on a laptop.

**Why it's interesting for John:**
- Memory mapping + lazy evaluation = process massive NHS datasets without crash
- Pandas-like API (smooth transition)
- Fast aggregations and filtering via C++ backend
- No need to spin up cloud instances for large historical data analysis

**NHS Use Case:** Analyze years of patient-level data (millions/billions of rows) without running out of memory or moving to cloud infrastructure.

**Relevance:** High — NHS datasets can be massive

---

## 4. SQLAI.ai — AI-Powered SQL Generation & Optimization

**URL:** https://www.sqlai.ai/

**What it is:** Transforms plain-English prompts into schema-aware SQL queries, plus automated query optimization with index recommendations.

**Why it's interesting for John:**
- Text-to-SQL: "Total referrals by trust for Q3 2024, excluding cancellations" → accurate SQL
- SQL Optimizer: Paste slow query → get optimized rewrites + index suggestions
- Explain-style diffs show exactly what changed
- Works with MySQL, PostgreSQL, SQL Server, BigQuery
- $6/month pricing makes it accessible

**NHS Use Case:** Speed up dashboard queries. Optimize slow Power BI report queries. Generate complex SQL from plain English requirements.

**Relevance:** Very High — direct SQL optimization need

---

## 5. Aiven AI Database Optimiser — Continuous SQL Performance Tuning

**URL:** https://console.aiven.io/

**What it is:** AI-powered database administrator that continuously scans workloads, identifies bottlenecks, and recommends optimizations for PostgreSQL and MySQL.

**Why it's interesting for John:**
- Automatic detection of slow queries
- Dynamic index recommendations that adapt to query patterns
- Real-time performance insights with CPU/I/O metrics
- Secure: analyzes only schema metadata, not sensitive data
- One-click optimization without deep DBA knowledge

**NHS Use Case:** Monitor NHS database performance automatically. Get alerts when queries degrade. Apply recommended optimizations during maintenance windows.

**Relevance:** High — NHS databases need continuous monitoring

---

## 6. pgBadger — PostgreSQL Log Analyzer (Free & Open Source)

**URL:** https://github.com/darold/pgbadger

**What it is:** Fast PostgreSQL log analyzer that parses logs and generates detailed performance reports.

**Why it's interesting for John:**
- Completely free and open source (~3.5K GitHub stars)
- Identifies slow queries, lock issues, and connection problems
- Generates HTML reports with charts and graphs
- No database access required — works purely from log files
- Very active maintenance

**NHS Use Case:** If NHS uses PostgreSQL (or similar), run pgBadger on logs to identify query performance issues without touching production databases.

**Relevance:** Medium-High — depends on NHS database stack

---

## 7. D-Tale — Interactive GUI for Pandas DataFrames

**URL:** https://github.com/man-group/dtale

**What it is:** Python library that launches an interactive web interface for exploring pandas DataFrames. Like Excel but for your notebook.

**Why it's interesting for John:**
- Sort, filter, explore DataFrames without writing code
- Built-in charting: histograms, correlations, custom plots
- Data cleaning and outlier detection
- Code export: actions generate equivalent pandas code
- Great for NHS stakeholders who prefer spreadsheet-style exploration

**NHS Use Case:** Let non-technical team members explore NHS data through a GUI while you keep full control via pandas.

**Relevance:** High — bridges gap between analysts and code

---

## Summary

| Tool | Category | NHS Relevance | Cost |
|------|----------|---------------|------|
| Pandera | Data Validation | High | Free |
| Sweetviz | EDA / Reporting | High | Free |
| Vaex | Large Data Processing | High | Free |
| SQLAI.ai | SQL Optimization | Very High | $6/mo |
| Aiven AI | DB Performance | High | Freemium |
| pgBadger | Log Analysis | Medium-High | Free |
| D-Tale | Interactive Exploration | High | Free |

**Top Pick:** SQLAI.ai — Direct hit on SQL optimization need, affordable, and produces explainable rewrites.

**Runner Up:** Sweetviz + Pandera combo — Free tools that dramatically improve data quality workflows.