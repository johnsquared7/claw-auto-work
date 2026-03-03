# Discovery: Modern Python Data Stack & Open Source BI for NHS Analysts
**Date:** 2026-03-03
**Source:** Autonomous discovery cycle (1600 UTC)
**Focus:** Python data analysis, BI alternatives, SQL optimization, report automation

---

## Key Findings

### 1. Evidence.dev — SQL-First Static Reports (Fresh Find)

**What it is:** A relatively new open-source BI tool that generates static HTML reports from Markdown + SQL queries.

**Why it's interesting for NHS workflow:**
- Reports are just `.md` files with embedded SQL — version controllable
- No database connection needed at view time — queries run at build time
- Perfect for scheduled PDF/HTML report generation
- No ongoing server costs — generates static files you can host anywhere

**Comparison to Power BI:**
- Power BI: Dynamic, interactive, requires Pro license for sharing
- Evidence: Static, markdown-based, free, no license headaches

**Real NHS use case:** Monthly performance reports that need to be emailed to stakeholders — build once, generate PDFs automatically via cron.

**Link:** https://evidence.dev/

### 2. Polars in Production — Django Migration Case Study

A recent case study (Feb 2026) showed a Django SaaS company replacing Pandas with Polars and achieving:
- **10x faster data processing** for dashboard queries
- **40% lower memory usage** on large dataset operations
- Direct compatibility with existing Pandas code patterns

**For NHS analysts:** If you're processing patient data extracts that make Excel crash, Polars can handle 10M+ rows without sweating.

**Key insight from search:** Major data engineering teams are now using "Polars for smaller stuff, PySpark only for huge datasets" — the middle ground is getting crowded out.

**Links:**
- https://medium.com/django-journal/replacing-pandas-with-polars-in-django-10x-faster-data-processing-for-saas-dashboards-a90c1af61dee

### 3. SQL Window Functions — The Hidden Productivity Booster

Window functions (`ROW_NUMBER()`, `RANK()`, `LAG()`, `LEAD()`) can replace complex self-joins and subqueries. For NHS data:

**Practical examples:**
```sql
-- Running totals (cumulative admissions)
SELECT 
    admission_date,
    daily_admissions,
    SUM(daily_admissions) OVER (ORDER BY admission_date) as cumulative
FROM daily_stats;

-- Compare current month to previous month
SELECT 
    month,
    admissions,
    LAG(admissions, 1) OVER (ORDER BY month) as prev_month
FROM monthly_data;

-- Rank departments by performance
SELECT 
    department,
    wait_times,
    RANK() OVER (ORDER BY wait_times DESC) as rank
FROM departments;
```

**Optimization tip from search results:** Define your window once and reuse it:
```sql
WITH ranking_window AS (ORDER BY score DESC)
SELECT 
    player_name, 
    RANK() OVER ranking_window AS rank_position,
    DENSE_RANK() OVER ranking_window AS dense_rank_position
FROM scores;
```

### 4. Open Source BI Comparison (2026)

| Tool | Best For | Architecture | AI Readiness | NHS Fit |
|------|----------|--------------|--------------|---------|
| **Apache Superset** | Big data/enterprise | Python/Flask | ⭐⭐⭐⭐⭐ | Good for trust-wide |
| **Metabase** | Quick insights | Java/React | ⭐⭐⭐ | Good for small teams |
| **Lightdash** | BI-as-Code | SQL/dbt | ⭐⭐⭐⭐ | If you use dbt already |
| **Evidence.dev** | Static reports | Markdown/SQL | ⭐⭐⭐ | **Best for automated PDF reports** |
| **Grafana** | Real-time | Go/TypeScript | ⭐⭐⭐⭐ | Good for operational dashboards |

### 5. AI-Assisted Data Analysis — Jupyter AI

Jupyter AI (extension for Jupyter Notebooks) can now:
- Auto-generate code for data preprocessing from uploaded datasets
- Suggest relevant algorithms automatically
- Generate complete ML model training code

**For NHS analysts who aren't coders:** This could help non-technical staff create basic analyses without writing Python.

---

## Action Items for John

| Tool | Relevance | Effort | Priority |
|------|-----------|--------|----------|
| Evidence.dev | High - automated PDF reports | Low | ⭐⭐⭐ |
| Polars | Medium - faster data processing | Medium | ⭐⭐ |
| Window functions | High - SQL productivity | Low | ⭐⭐⭐ |
| Superset | Medium - trust-wide dashboards | High | ⭐⭐ |

---

## Saved Links

- https://evidence.dev/ - SQL-first static reports
- https://medium.com/django-journal/replacing-pandas-with-polars-in-django-10x-faster-data-processing-for-saas-dashboards-a90c1af61dee - Polars migration case study
- https://last9.io/blog/sql-query-optimization/ - SQL optimization techniques
- https://www.c-sharpcorner.com/article/sql-window-functions-explained-examples-best-practices2/ - Window functions guide
- https://aixoria.com/5-best-business-intelligence-open-source-tools-complete-2026-guide/ - Open source BI comparison
- https://dasroot.net/posts/2026/03/emerging-python-use-cases-2026/ - Emerging Python use cases

---

## Why These Matter for NHS Workflow

1. **Evidence.dev** fills a gap: automated, scheduled, static reports without licensing costs
2. **Polars** is the pandas replacement everyone's migrating to — good for future-proofing
3. **Window functions** are underused by analysts who learned SQL the hard way — massive time saver
4. **Open source BI** alternatives are mature now — no reason to pay for Power BI if you're doing static reporting

---
*Discovery cycle complete. Next run: 1800 UTC.*
