# Discovery: Python Data Stack for NHS Analytics
**Date:** 2026-03-03
**Source:** Autonomous discovery cycle

---

## Key Findings

### 1. DuckDB - The "SQL on Dataframes" Game Changer
DuckDB is gaining serious traction as a complement to Pandas, not replacement. Key insight for NHS workflow:
- Runs full SQL queries on CSV/Parquet files without loading into memory
- Perfect for those "just need to query this large extract" moments
- Integrates natively with Pandas: `df.to_duckdb()` then query with SQL
- **Use case:** Quick SQL queries on 100MB+ patient data extracts without Excel crashing

### 2. Polars Rising
Polars (Rust-based) is positioning itself as the fast alternative to Pandas:
- Lazy evaluation by default - builds query plan before execution
- 10-100x faster for large datasets
- Native Python API (no JVM like PySpark)
- **NHS use case:** Scheduled overnight reports that process millions of rows

### 3. NHS Python Community (nhs-pycom.net)
Active community specifically for Python in healthcare:
- NHS-R community resources for analytics
- Synthetic data generation tools
- Statistical process control (SPC) charts auto-generated
- Google Health partnership on NHS time-of-travel analysis

### 4. Auto-SQL for Clinical Staff
Interesting PMC paper on drag-and-drop SQL generation for non-technical clinical staff:
- Hierarchical tree structure → widgets → auto-generated SQL
- Enables complex queries without SQL knowledge
- **Relevance:** Could reduce analyst workload for routine extractions

### 5. Power BI Alternatives for Healthcare
Search didn't reveal specific healthcare-focused BI alternatives, but the trend is:
- **Apache Supabase** (open source) - Postgres-based, good for Python integration
- **DuckDB + Streamlit** - emerging as lightweight BI replacement
- **Evidence** - SQL-first static reports, markdown + SQL

---

## Action Items for John

| Tool | Relevance | Effort |
|------|-----------|--------|
| DuckDB | High - drop-in for heavy Excel workflows | Low |
| Polars | Medium - future-proofing, speed | Medium |
| nhs-pycom | High - community + templates | Low |
| Streamlit reporting | Medium - quick dashboards | Medium |

---

## Saved Links

- https://nhs-pycom.net/ - NHS Python Community
- https://motherduck.com/blog/duckdb-versus-pandas-versus-polars/ - Comparison guide
- https://pmc.ncbi.nlm.nih.gov/articles/PMC9306316/ - Auto-SQL for healthcare
- https://github.com/topics/nhs - NHS GitHub topics (SPC charts, etc.)
