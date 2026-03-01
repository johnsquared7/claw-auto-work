# Discovery: NHS Analyst Tools & Techniques
**Date:** 2026-03-01
**Source:** Autonomous web discovery

---

## 🔥 Key Findings

### 1. DuckDB - The Rising Star for Single-Node Analytics
DuckDB is being described as "redefining single-node analytics" in 2026. It's a high-performance analytical SQL database that runs entirely in-process - no server needed. Perfect for analysts who want speed without infrastructure overhead.

**Why it matters:** Fast parquet/csv analysis, zero config, SQL interface. Could replace heavier solutions for NHS ad-hoc analysis.

**URL:** https://duckdb.org/

---

### 2. Apache Iceberg - Lakehouse Standard
Iceberg is leading the "lakehouse revolution" - bringing ACID transactions to data lakes. If John is working with large datasets, this is becoming the standard format.

**Why it matters:** Reliable tabular data storage, time travel, schema evolution. Key for healthcare data that needs audit trails.

---

### 3. Metabase 2026 - Self-Service Analytics Leap
Metabase's 2026 version has "significantly advanced its self-service analytics" - includes better AI-powered insights and easier dashboard building.

**Why it matters:** Free, open-source BI that's easier than Power BI. Great for sharing NHS reports with non-technical stakeholders.

**URL:** https://www.metabase.com/

---

### 4. Apache Superset - Scale + AI
Superset now handles scale "better than most lightweight BI tools" with full AI Lab integrations and semantic layer compatibility.

**Why it matters:** If Metabase feels too limited, Superset is the next step up - still free and open source.

**URL:** https://superset.apache.org/

---

### 5. AI SQL Optimizers (Game Changers)

**EverSQL** (https://www.eversql.com/):
- Automatic PostgreSQL/MySQL optimization
- Recommends index deletions, schema changes
- Reduces CPU, memory, storage costs

**Aiven AI Database Optimizer**:
- PostgreSQL/MySQL query analysis
- AI reviews query logic, joins, indexes
- Provides optimized rewrites + index creation
- Shows query diffs

**SQLAI.ai** (https://www.sqlai.ai/sql-optimizer):
- Free AI-powered SQL optimizer
- Full performance analysis per database engine

**Why it matters:** These can 5-10x query performance without manual tuning - huge for slow NHS reports.

---

### 6. NHS Python Community (Goldmine)
**nhs-pycom.net** is the community site for Python in the NHS. They have:

- **nhs-number** package: Python utilities for NHS number validation, normalisation, generation
  - GitHub: https://github.com/uk-fci/nhs-number
  
- NHS-themed analytics templates using Python + Plotly + GitHub Pages
- Synthetic data generation projects
- Discrete event simulation and agent-based modelling resources

**Why it matters:** Directly relevant to NHS workflow - validated NHS number handling, reusable templates.

---

### 7. NHS Analytics DART
NHS England's open analytics projects template:
- NHS.uk themed templates
- Build end-to-end analytical tools with Python, Plotly, GitHub.io, GitHub Actions
- GitHub: https://nhsx.github.io/AnalyticsUnit/projects.html

**Why it matters:** Ready-made framework for publishing NHS-facing analytical tools.

---

## 📋 Recommendations for NHS Analyst Workflow

1. **Try DuckDB** for fast local analysis of CSV/Parquet NHS data
2. **Set up Metabase** as free Power BI alternative for team dashboards
3. **Use nhs-number** package for validating NHS numbers in Python pipelines
4. **Test EverSQL** on slow PostgreSQL queries (free tier available)
5. **Explore DART templates** if building public-facing NHS analytics

---

## Tags
#python #data-analysis #nhs #healthcare #sql-optimization #bi-tools #duckdb #metabase
