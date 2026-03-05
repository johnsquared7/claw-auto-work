# Discovery: Polars, SQL Optimization & Open-Source BI — March 2026

**Date:** 2026-03-05  
**Category:** Python Data Analysis / SQL Optimization / BI Tools  
**Quality:** High — ecosystem shifts and practical tools with NHS workflow relevance

---

## TL;DR

5 discoveries for John's NHS analyst workflow:
1. **Polars** — The pandas alternative gaining serious momentum in 2026
2. **DuckDB** — SQL-first analytics database (works directly on CSV/Parquet)
3. **Metabase AI** — Free, open-source BI with embedded AI query assistance
4. **Apache Superset 2026** — Enterprise-grade open-source BI
5. **dbForge SQL Tools** — Specialized SQL Server optimization suite

---

## 1. Polars — The Fast DataFrame Library That's Winning

**Website:** https://docs.kanaries.net/articles/polars-vs-pandas  
**What:** Rust-based DataFrame library now competing head-to-head with Pandas

**Why it matters for NHS:**
- **10-50x faster** than Pandas for large datasets (common in NHS data)
- Lazy evaluation — builds query plan before executing (like Spark)
- Better memory efficiency — critical when working with large NHS datasets on limited hardware

```python
import polars as pl

# Equivalent pandas operations in Polars
df = pl.read_csv("waiting-list.csv")
result = (
    df.lazy()
    .filter(pl.col("wait_weeks") > 52)
    .group_by("trust_code")
    .agg(pl.col("patient_id").count().alias("long_waiters"))
    .sort("long_waiters", descending=True)
    .collect()
)
```

**Key Insight (March 2026):** The Python data ecosystem is converging on **Apache Arrow** as the common memory format. This means:
- Polars ↔ Pandas interoperability is seamless
- DuckDB, Polars, and other tools can share data without copying
- The "Arrow ecosystem" is becoming the standard

**Recommendation:** For new NHS projects, try Polars. For existing Pandas code, use `pandas.DataFrame.to_pandas()` to convert when needed.

---

## 2. DuckDB — The SQL Database That Reads Files Directly

**Website:** https://duckdb.org/  
**What:** In-process SQL OLAP database that runs queries directly on CSV, Parquet, JSON files

**Why it matters for NHS:**
- No need to load data into a database first — query files directly
- PostgreSQL-compatible SQL syntax
- Can join across multiple file formats in a single query
- Embeddable — no server setup required

```python
import duckdb

# Query a CSV file directly with SQL
result = duckdb.execute("""
    SELECT trust_name, 
           COUNT(*) as total_admissions,
           AVG(length_of_stay) as avg_los
    FROM 'hospital-data-2025.csv'
    WHERE admission_method = 'Emergency'
    GROUP BY trust_name
    ORDER BY total_admissions DESC
    LIMIT 10
""").df()

# Join CSV with Parquet in same query
result = duckdb.execute("""
    SELECT a.*, b.waiting_list_size
    FROM 'admissions.csv' a
    JOIN 'trust-metrics.parquet' b ON a.trust_code = b.code
""").df()
```

**Use case for John:** Replace complex pandas merge operations with SQL queries that work directly on files. Much faster for large NHS datasets.

---

## 3. Metabase AI — Free BI with Embedded AI Assistant

**Website:** https://www.metabase.com/  
**What:** Open-source business intelligence tool with new AI features in 2026

**Why it matters for NHS:**
- **Free and open-source** (self-host option)
- AI-powered query builder — describe what you want in plain English
- No SQL required for basic queries
- Can connect to PostgreSQL, MySQL, and NHS data sources

**New in 2026:**
- Metabase AI assistant that generates SQL from natural language
- Automatic data visualization recommendations
- Semantic layer for defining NHS metrics consistently

**Comparison:**
| Feature | Power BI | Metabase |
|---------|----------|----------|
| Cost | Paid (£10+/user/mo) | Free (open source) |
| AI Queries | Premium | Emerging |
| NHS Data Sources | ✅ | ✅ |
| Self-host | ❌ | ✅ |

**Action:** Could be a free alternative for NHS teams who can't afford Power BI Pro.

---

## 4. Apache Superset 2026 — Enterprise Open-Source BI

**Website:** https://superset.apache.org/  
**What:** Cloud-native business intelligence platform used by Airbnb, Udemy, and growing in healthcare

**Why it matters for NHS:**
- **Completely free and open-source**
- Modern UI — comparable to Tableau
- Can connect to PostgreSQL, MySQL, and any SQLAlchemy source
- **Semantic layer** for defining calculated metrics
- Good for embedding dashboards in other apps

**2026 Updates:**
- Improved AI/ML integration
- Better mobile support
- Enhanced caching for faster dashboard loading

**vs Metabase:**
| Feature | Superset | Metabase |
|---------|----------|----------|
| Learning curve | Steeper | Easier |
| Customization | More | Less |
| Visualizations | 50+ | 15+ |
| Best for | Power users | Casual users |

---

## 5. dbForge SQL Tools — SQL Server Optimization Suite

**Website:** https://www.devart.com/dbforge/sql-toolkit/  
**What:** Specialized SQL Server tools for query optimization and debugging

**Why it matters for NHS:**
- **Query Profiler** — Visualize query execution plans
- **Index Manager** — Analyze and suggest missing indexes
- **Query Builder** — Visual SQL construction
- Works with SQL Server and Azure SQL

**Features:**
- Compare query execution plans side-by-side
- Identify missing indexes with impact estimates
- Analyze query performance over time
- Test query changes without affecting production

**Cost:** Paid (~£150/year) but has free trial. Could be worth it for intensive SQL optimization work.

**Alternative (Free):** SQL Server's built-in **Execution Plan Analysis** and **Database Engine Tuning Advisor** — less polished but functional.

---

## Priority Recommendation for John

| Priority | Tool | Effort to Try | NHS Impact |
|----------|------|---------------|------------|
| 1 | **DuckDB** | Low (pip install) | High — replaces complex pandas file ops |
| 2 | **Polars** | Medium (learn syntax) | High — speed for large NHS datasets |
| 3 | **Metabase** | Medium (self-host) | Medium — free Power BI alternative |
| 4 | **Superset** | Higher (setup) | Medium — enterprise BI needs |
| 5 | **dbForge** | Low (free trial) | Low — only if SQL Server heavy |

---

## Key Trend: The Arrow Ecosystem Convergence

The biggest insight from March 2026 research:

> The Python data ecosystem is consolidating around **Apache Arrow** as the common in-memory format.

This means:
- **Polars, Pandas, DuckDB, and PyArrow** all interoperate seamlessly
- Data can flow between tools without copying/conversion overhead
- Future-proof your workflow by choosing Arrow-compatible tools

For John's NHS workflow: **DuckDB + Polars** together = extremely fast local analytics without database infrastructure.

---

## Sources

- Kanaries: "Polars vs Pandas: Which DataFrame Library Should You Use in 2026?"
- DuckDB Documentation: https://duckdb.org/docs
- Metabase Blog: "Metabase AI Assistant"
- Apache Superset: 2026 release notes
- Brent Ozar: SQL Server performance monitoring tools
- Monte Carlo Data: "Top Open Source BI Tools In 2026"
