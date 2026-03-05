# Discovery — 2026-03-05 14:00 UTC

## Theme: NHS Data Analysis & SQL Optimization

---

### 1. NHS Digital Analytics Services — Goldmine Repo

**URL:** https://github.com/NHSDigital/data-analytics-services

**What it is:** Official NHS England open-source analytics repo with 20+ projects.

**Why it's interesting:**
- **codonPython** - Reduces barriers for new NHS analysts learning Python
- **Medicines text mining tool** - Python/PySpark for mining medicines data
- **Artificial Data Generator** - Generate anonymized synthetic NHS data in Databricks
- **DNAttend** - ML framework for predicting patient non-attendance (Python)
- **MedicalMap** - Streamlit app for interactive healthcare mapping (NHS Python Community + Google Health)
- **Forecasting** - Multiple forecasting methods for healthcare
- **MultiNet** - CLI tool for multi-morbidity network analysis

**Relevance:** Direct source of NHS-proven Python patterns, ETL pipelines, and data quality approaches.

---

### 2. Tuva Health — Healthcare Data Model

**URL:** https://github.com/tuva-health/tuva

**What it is:** Open-source healthcare data model with core data marts, data quality tests, and terminology sets.

**Why it's interesting:**
- Core data model for healthcare (similar to OMOP but open)
- Data quality tests included
- Terminology sets built-in
- dbt integration for transformations
- Active development (updated Mar 2026)

**Relevance:** Could standardize how John structures NHS data for analysis — similar to what NHS Data Analytics Services uses internally.

---

### 3. SQL Optimization Tools (5-10x Performance)

**Source:** Medium article testing 40+ tools across Snowflake, BigQuery, Postgres, Redshift

**Top picks for NHS context:**

| Tool | Best For |
|------|----------|
| **pgBadger** | PostgreSQL query analysis (free, Perl-based) |
| **pg_stat_statements** | Built-in Postgres performance tracking |
| **SQLFlash** | AI-powered SQL optimization (2025) |
| **Azure SQL Intelligent Performance** | Auto-tuning for SQL Server |

**Key techniques:**
- CTE vs subquery optimization
- Index strategy for date columns (common in NHS)
- Partitioning for large tables
- Execution plan analysis

**Relevance:** NHS databases often have complex joins across large tables — these tools could speed up monthly reporting.

---

### 4. Power BI Alternatives — Current State 2026

**Comparison for NHS analyst:**

| Tool | Pros | Cons |
|------|------|------|
| **Metabase** | Easiest for self-service, embedded analytics | Less customization |
| **Apache Superset** | Most powerful, SQL-focused, Python viz | Steeper learning curve |
| **Streamlit** | Fastest dev, Python-only, great for internal tools | Not great for non-technical users |
| **Evidence** | Markdown-driven, SQL queries, modern alternative | Newer, smaller community |

**Reddit consensus (Dec 2024/2025):**
- "Metabase and Grafana best for beginners"
- "Superset great for technical users comfortable with SQL and Python"
- "Streamlit: first working draft in couple hours with ChatGPT"

**Relevance:** John's learning Python — Streamlit + SQL could replace simple Power BI reports quickly.

---

### 5. SQL in 2025 — AI Integration

**Key trend:** Major databases now integrate AI for query optimization:
- **Azure SQL Database** — continuous performance tuning via ML
- **BigQuery** — automatic query optimization
- **AI2sql** — natural language to SQL, plus AI optimization suggestions

**Relevance:** Could reduce time spent manually tuning queries.

---

## Action Items for John

1. **Explore NHS Digital repos** — especially `codonPython` for learning path
2. **Try Tuva Health** — if starting new data pipeline project
3. **Test pgBadger** — if using PostgreSQL for NHS data
4. **Experiment with Streamlit** — for quick internal dashboards replacing simple PBI reports

---

*Discovery cycle: 2026-03-05 14:00 UTC*
