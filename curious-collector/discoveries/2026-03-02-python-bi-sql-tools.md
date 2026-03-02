# Discovery: Python Data Analysis & BI Tools for NHS Workflow
**Date:** 2026-03-02
**Category:** Python Data Analysis, BI Tools, SQL Optimization

---

## 1. Polars - The 2026 DataFrame Standard

**Why it's interesting:** Polars is emerging as the definitive replacement for Pandas in 2026 for medium-to-large datasets.

**Key insights:**
- **Performance:** 5-10x faster than Pandas via multithreaded execution
- **Lazy evaluation:** Composable pipelines that optimize execution automatically
- **Stricter API:** Fewer schema-related bugs, more explicit data transformations
- **Zero-copy DuckDB integration:** Can query Polars DataFrames via SQL without copying data

**For NHS workflow:** If John's data analysis involves >10k rows, Polars will dramatically speed up ETL and reporting pipelines.

**Links:**
- https://docs.pola.rs/user-guide/misc/comparison/
- https://pola.rs/posts/benchmarks/

---

## 2. DuckDB + Ibis - SQL on DataFrames

**Why it's interesting:** DuckDB is an in-process SQL OLAP database that pairs perfectly with Polars.

**Key insights:**
- **Zero-copy interoperability:** Query Polars DataFrames directly via SQL
- **Single-node OLAP:** Think of it as "SQLite for analytics" - no server needed
- **Ibis project:** Provides SQL-like syntax that compiles to Polars, DuckDB, Pandas, and more

**For NHS workflow:** John could write SQL queries against his NHS data exports without setting up a full database server.

**Links:**
- https://duckdb.org/docs/guides/python/polars.html

---

## 3. Apache Superset - Open Source BI

**Why it's interesting:** Mature open-source alternative to Power BI, used by Airbnb, Netflix, and others.

**Key insights:**
- **Free & open source:** No licensing costs
- **SQL-based:** Connect to any SQL database (including NHS data sources)
- **Rich visualisations:** 90+ visualization types
- **Self-hosted:** Full control over data (important for NHS compliance)

**For NHS workflow:** Could replace Power BI for dashboarding with zero cost.

**Links:**
- https://superset.apache.org/

---

## 4. Metabase - User-Friendly BI

**Why it's interesting:** Simpler than Superset, great for non-technical users.

**Key insights:**
- **Question builder:** Non-SQL users can drag-and-drop queries
- **Embeddable:** Can embed dashboards in other apps
- **SQL interface:** For analysts who want raw queries

**For NHS workflow:** Could hand off to managers who need self-service reporting without learning SQL.

**Links:**
- https://www.metabase.com/

---

## 5. EverSQL - AI SQL Optimization

**Why it's interesting:** AI-powered query optimization for PostgreSQL and MySQL.

**Key insights:**
- **Automatic indexing suggestions:** Identifies missing indexes
- **Query rewriting:** AI suggests better query structures
- **Schema optimization:** Recommendations for table redesign

**For NHS workflow:** If John works with PostgreSQL databases, EverSQL could speed up slow queries.

**Links:**
- https://www.eversql.com/

---

## 6. SQLAI.ai - Free Online SQL Optimizer

**Why it's interesting:** Quick free tool for optimizing individual queries.

**Key insights:**
- **Free tier:** Optimise queries without signup
- **Supports multiple databases:** MySQL, PostgreSQL, SQL Server, Oracle
- **AI-powered:** Rewrites queries for better performance

**For NHS workflow:** Quick wins on slow SQL reports.

**Links:**
- https://www.sqlai.ai/sql-optimizer

---

## Recommendation for NHS Analyst Workflow

**Priority 1: Try Polars**
- Drop-in performance improvement for existing Pandas code
- Use `narwhals` library as bridge if migrating gradually

**Priority 2: Set up DuckDB for ad-hoc SQL**
- No database server needed
- Perfect for analyzing CSV/Excel exports from NHS systems

**Priority 3: Explore Superset**
- If Power BI licensing is a concern
- Self-hosted option for NHS data compliance

**Priority 4: Use SQLAI.ai**
- Quick query optimizations for immediate gains

---

*Discovery made: 2026-03-02*
