# Discovery: 2026-03-02

**Focus:** Python data analysis, Power BI alternatives, SQL optimization, report automation

---

## 1. Evidence.dev — Notebook-Style BI as Code

**What:** Open-source framework that builds BI websites from Markdown + SQL files.

**Why it's interesting for John:**
- Write reports in Markdown with embedded SQL queries
- Version control your reports like code
- No drag-and-drop → reproducible, auditable reports
- Supports PostgreSQL, MySQL, Snowflake, SQLite + CSV/Parquet files
- Generates static sites or self-hosted dashboards

**Use case for NHS workflow:**
- Create weekly/monthly KPI reports as Markdown files
- SQL queries run at build time → no manual data refresh needed
- Perfect for automated report generation pipelines

**GitHub:** [evidence-dev/evidence](https://github.com/evidence-dev/evidence)

---

## 2. DuckDB — Embedded OLAP for Python

**What:** In-process SQL OLAP database, embedded in Python apps.

**Why it's interesting for John:**
- No server setup → just `pip install duckdb`
- Query CSV, Parquet, JSON files directly with SQL
- 10-100x faster than pandas for analytical queries on large files
- Columnar storage optimized for aggregations
- Works perfectly with pandas DataFrames

**Use case for NHS workflow:**
- Load large NHS datasets (millions of rows) locally
- Run complex analytical queries without a full database server
- Prototype ETL pipelines before moving to production SQL Server

**Links:**
- [duckdb.org](https://duckdb.org/)
- [Article: Speeding Up In-Process Analytics With Python](https://www.opensourceforu.com/2026/02/duckdb-speeding-up-in-process-analytics-with-python/)

---

## 3. Streamlit — Fastest Path from Data to Dashboard

**What:** Python framework for building data apps in minutes.

**Why it's interesting for John:**
- Pure Python → no HTML/CSS needed
- Auto-reloads on code change
- Built-in support for charts, tables, forms
- Great for internal tools and quick prototypes

**Comparison (2026):**
| Feature | Streamlit | Dash | Shiny |
|---------|-----------|------|-------|
| Speed to prototype | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐ |
| Customization | ⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐ |
| Deployment | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐ |
| Python-only | Yes | Yes | R |

**Recommendation for John:** Start with Streamlit for internal NHS dashboards. Switch to Dash if you need more control.

---

## 4. SQL Optimization Tools — 2026 Landscape

**Key tools found:**

| Tool | Type | Best For |
|------|------|----------|
| **EXPLAIN ANALYZE** | Built-in | Query plan analysis (all major DBs) |
| **pg_stat_statements** (PostgreSQL) | Extension | Identify slow queries |
| **SQLFluff** | Linter | SQL style + basic performance hints |
| **SQLAI.ai** | AI Tool | Query generation + optimization ($6/mo) |
| **Metis** | Commercial | Automatic index recommendations |

**For NHS SQL Server:**
- Use Execution Plan analyzer
- Consider `sys.dm_exec_query_stats` for query performance tracking

---

## 5. Power BI Alternatives — Quick Overview

| Tool | Type | Self-Hosted | Free Tier |
|------|------|--------------|-----------|
| **Apache Superset** | Full BI | ✅ | ✅ |
| **Metabase** | Full BI | ✅ | ✅ |
| **Redash** | Query + Viz | ✅ | ✅ |
| **Evidence** | Notebook-style | ✅ | ✅ |
| **Grafana** | Dashboards | ✅ | ✅ |

**Recommendation for John:** Metabase is easiest for NHS teams (low learning curve). Evidence for code-driven reports.

---

## 6. Report Automation Patterns

**Python tools for scheduled reports:**
- ** schedule** — Simple cron-like scheduling in Python
- **python-dotenv** — Store credentials safely
- **sqlalchemy** + **pyodbc** — Connect to NHS SQL Server
- **jinja2** — Template-based report generation
- **weasyprint** — Convert HTML/Pandas tables to PDF

**Basic pattern:**
```
1. SQL query → pandas DataFrame
2. Jinja2 template + data → HTML report
3. weasyprint → PDF
4. smtplib/email → Send to distribution list
```

---

## Quality Check

All items above are:
- ✅ Actively maintained (2025-2026 activity)
- ✅ Relevant to NHS analyst workflow
- ✅ Have free/self-hosted options
- ✅ Not generic "AI news" — specific tools with concrete use cases

---

*Discovery cycle: 2026-03-02*
