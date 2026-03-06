# Discovery: Python Data Quality & SQL Optimization Tools
**Date:** 2026-03-06 04:00 UTC
**Focus:** NHS analyst workflow - data validation, SQL performance, pandas alternatives

---

## 1. Pandera - DataFrame Schema Validation

**What:** Statistical data validation library for pandas DataFrames with type-hinting and schema validation.

**Why it matters for NHS:**
- Validate incoming data extracts against expected schemas
- Catch data quality issues before they propagate to reports
- Define expected column types, value ranges, and statistical properties
- Integrates with pandas pipelines - drop-in validation

**Link:** https://pandera.readthedocs.io/

**Example use case:** Validate Trust-level performance data - ensure `trust_code` is string, `admissions` is int, `wait_time_days` is within expected range (0-365).

---

## 2. Pyjanitor - Clean Method Chaining for Data Cleaning

**What:** Extends pandas with a clean, method-chaining API for data cleaning operations.

**Why it matters for NHS:**
- Chainable data cleaning - `.clean_names().remove_empty().fill_missing()`
- Auto-convert column names to snake_case
- Built-in functions for common cleaning tasks
- Makes data prep code more readable and maintainable

**Link:** https://pyjanitor-devs.github.io/pyjanitor/

**Key methods:**
- `clean_names()` - normalize column names
- `remove_empty()` - drop empty columns
- `get_dupes()` - identify duplicate rows
- `fill_missing()` - smart NA handling

---

## 3. Sweetviz - Automated EDA Reports

**What:** Generates comprehensive HTML EDA reports with target analysis and dataset comparisons.

**Why it matters for NHS:**
- Instant profiling of new data extracts
- Compare training vs test sets, or before/after transformations
- Target analysis shows feature relationships to outcome variable
- Great for stakeholder-ready data documentation

**Link:** https://github.com/fbdesignpro/sweetviz

**Output:** Self-contained HTML with correlation matrices, distribution plots, and association analysis.

---

## 4. ITables - Interactive Jupyter Tables

**What:** Brings DataTables.js interactivity to Jupyter notebooks - search, sort, paginate large DataFrames.

**Why it matters for NHS:**
- Explore large datasets in notebooks without crashing
- Search, sort, filter with point-and-click
- Only renders visible rows - keeps notebooks responsive
- Great for ad-hoc data exploration during analysis

**Link:** https://mwouts.github.io/itables/quick_start.html

---

## 5. pgBadger - PostgreSQL Log Analyzer

**What:** Fast PostgreSQL log analyzer that generates detailed reports on queries, errors, and performance.

**Why it matters for NHS:**
- Identify slow queries from production logs
- Query statistics by database, user, application
- Visual reports on query performance over time
- Free, command-line tool - easy to integrate

**Link:** https://github.com/darold/pgbadger

**Use case:** Run weekly on NHS data warehouse logs to surface top 10 slowest queries for optimization.

---

## 6. EverSQL - AI SQL Query Optimizer

**What:** Non-intrusive SQL optimization that monitors PostgreSQL/MySQL and generates optimization recommendations.

**Why it matters for NHS:**
- Automatic query analysis and index suggestions
- Supports PostgreSQL and MySQL
- Non-intrusive sensor approach
- Shows before/after query plans

**Link:** https://www.eversql.com/

**Free tier:** Basic query optimization and index recommendations.

---

## 7. SQLAI.ai - Free AI SQL Optimizer

**What:** AI-powered SQL optimization that analyzes queries and suggests performance improvements.

**Why it matters for NHS:**
- Paste slow queries, get optimized versions
- Explains why changes improve performance
- Supports multiple database engines
- Free to use

**Link:** https://www.sqlai.ai/sql-optimizer

---

## 8. awesome-pandas-alternatives - Curated DataFrame Library List

**What:** Comprehensive comparison of pandas alternatives with performance characteristics.

**Key libraries for NHS analyst work:**

| Library | Strength | When to Use |
|---------|----------|-------------|
| **Polars** | Fast, lazy evaluation | Large files, complex pipelines |
| **DuckDB** | SQL on local files | Query CSV/Parquet without loading |
| **Vaex** | Out-of-core processing | Billion-row datasets on laptop |
| **cuDF** | GPU acceleration | 50-100x speedup on compatible hardware |

**Link:** https://github.com/baggiponte/awesome-pandas-alternatives

---

## Actionable Takeaways for NHS Analyst Workflow

### Data Quality Pipeline
```
1. Use Pandera to define expected schema for incoming data
2. Chain Pyjanitor methods for cleaning
3. Generate Sweetviz report for documentation
```

### SQL Performance
```
1. Run pgBadger weekly on warehouse logs
2. Paste slow queries into SQLAI.ai or EverSQL
3. Implement suggested indexes
```

### Large Data Handling
```
1. Switch to Polars for files >1M rows
2. Use DuckDB for ad-hoc SQL on CSV files
3. Consider Vaex for datasets that don't fit in RAM
```

---

## Sources
- KDnuggets: 10 Lesser-Known Python Libraries for Data Science (2026)
- Medium: 15 SQL Optimization Tools That Make Queries 10x Faster
- GitHub: awesome-pandas-alternatives
- EverSQL, SQLAI.ai documentation