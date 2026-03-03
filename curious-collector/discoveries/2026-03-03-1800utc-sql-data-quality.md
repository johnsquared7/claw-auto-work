# Discovery: SQL Optimization & Data Quality Tools for NHS Analyst
**Date:** 2026-03-03
**Time:** 1800 UTC
**Source:** Autonomous discovery cycle
**Focus:** SQL optimization, data validation, large-scale data handling

---

## Key Findings

### 1. SQL Optimization Tools (Practical for NHS Work)

| Tool | What It Does | Relevance |
|------|--------------|-----------|
| **pgBadger** | PostgreSQL log analyzer - visualizes slow queries, highlights missing indexes | High if NHS uses Postgres |
| **EverSQL** | AI-powered SQL optimizer for PostgreSQL & MySQL. Suggests index additions, rewrites | Free tier available |
| **SQLAI.ai** | LLM-based SQL optimizer - paste query, get improved version | Free online tool |
| **SolarWinds Plan Explorer** | Visual query plan analyzer for SQL Server | High if NHS uses MSSQL |
| **EXPLAIN ANALYZE** | Built-in Postgres query profiling - underused but powerful | Free, immediate |

**For John's workflow:** If he's running queries against MSSQL/Postgres in NHS, EverSQL or Plan Explorer could cut report generation time significantly.

### 2. Data Quality & Validation (Critical for Clinical Data)

**Pandera** - Statistical data validation library:
- Define schemas for pandas DataFrames with type hints
- Validates value ranges, statistical properties
- Error messages tell you exactly what failed and where
- Integrates into ETL pipelines to catch bad data before reports run

```python
import pandera as pa

schema = pa.DataFrameSchema({
    "patient_id": pa.Column(pa.String, pa.Check.str_length(10)),  # NHS number format
    "age": pa.Column(pa.Int, pa.Check.between(0, 120)),
    "admission_date": pa.Column(pa.DateTime),
})
```

**Great Expectations** - More enterprise-grade data validation:
- Data docs with interactive HTML reports
- Automated profiling from existing data
- Expectation suites that can be version-controlled

**For John's workflow:** Essential for automated report pipelines - catch data quality issues before they reach stakeholders.

### 3. Large Dataset Handling (Vaex)

**Vaex** - Out-of-core DataFrames for billion-row datasets:
- Memory-mapped files - doesn't load data into RAM
- Works on datasets larger than available memory
- Familiar pandas-like API
- Fast aggregations on lazy expressions

**Use case:** NHS patient extracts with millions of rows won't crash Excel or pandas.

```python
import vaex
df = vaex.open('large_nhs_extract.parquet')
# SQL-like queries without loading into memory
result = df.groupby('region', agg={'waiting_list': 'sum'})
```

### 4. Interactive Data Exploration (D-Tale)

**D-Tale** - GUI for pandas DataFrames:
- Spreadsheet-like interface in browser
- Built-in charts (histograms, correlations)
- Code export - generates pandas code from your clicks
- No setup required - drop into any script

```python
import dtale
dtale.show(df)
```

### 5. Report Automation Patterns

- **Quart** / **FastAPI** - Python web frameworks for scheduled report APIs
- **schedule** library - simple cron-like scheduling
- **WeasyPrint** - HTML to PDF conversion (NHS report formatting)
- **Jinja2 + pandas** - Templated Excel/Word reports

---

## Action Items for John

| Tool | Priority | Effort |
|------|----------|--------|
| Pandera | High - data validation in pipelines | Low |
| Vaex | Medium - large NHS extracts | Low |
| EverSQL | High - query optimization | Low (online) |
| D-Tale | Medium - quick EDA | Low |

---

## Saved Links

- https://github.com/darold/pgbadger - PostgreSQL log analyzer
- https://www.eversql.com/ - AI SQL optimizer
- https://pandera.readthedocs.io/ - Data validation
- https://vaex.io/ - Large dataset handling
- https://github.com/man-group/dtale - Interactive DataFrames
- https://www.greatexpectations.io/ - Enterprise data validation

---

*Discovery cycle complete - 1800 UTC*
