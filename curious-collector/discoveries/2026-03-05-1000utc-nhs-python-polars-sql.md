# Discovery — March 5, 2026 — 1000 UTC

## Relevant to: John's NHS analyst workflow (Python, Power BI alternatives, SQL, report automation)

---

## 🔥 Top Discovery: Polars — The Fast Pandas Alternative

**What:** High-performance DataFrame library written in Rust, now the standard for large-scale data processing.

**Why it's interesting:**
- **10-100x faster than pandas** for most operations
- Uses **lazy evaluation** — builds query plan before execution, optimizes automatically
- Handles **10GB-100GB+ datasets** that would crash RAM-limited machines
- Better API design than pandas (fewer gotchas)
- Works with pandas: `pl.from_pandas()` / `to_pandas()`

**For NHS workflow:**
- Perfect for large patient datasets
- Lazy evaluation means queries only run when needed — saves memory
- Integrates with Python ecosystem (pandas, numpy, matplotlib)

**Code comparison:**
```python
# Pandas
df.groupby('department').agg({'waiting_time': 'mean'})

# Polars (lazy)
(pl.LazyFrame(df)
  .group_by('department')
  .agg(pl.col('waiting_time').mean())
  .collect())  # executes only when called
```

**Verdict:** 💡 If John is processing large NHS datasets, Polars is worth the switch. Lower memory, faster, cleaner API.

---

## 📊 ydata-profiling (formerly pandas-profiling)

**What:** One-line EDA reports — generates comprehensive HTML with statistics, correlations, missing values, distributions.

**Why it matters:**
- **30 seconds** vs hours of manual EDA
- Perfect for initial data quality checks on NHS datasets
- Detects: missing values, duplicates, correlations, skewness
- Exports to HTML/JSON for sharing

```python
from ydata_profiling import ProfileReport

profile = ProfileReport(df, title="NHS Waiting Times Report")
profile.to_file("waiting_times.html")
```

**Verdict:** 💡 Great for quick data quality audits on new NHS datasets.

---

## 🏥 SQL Server Optimization for Healthcare

**Key techniques from latest research:**

### 1. Table Partitioning
```sql
-- Partition by date for time-series healthcare data
CREATE PARTITION FUNCTION pf_EncounterDate (datetime)
AS RANGE RIGHT FOR VALUES ('2024-01-01', '2025-01-01', '2026-01-01');

CREATE PARTITION SCHEME ps_EncounterDate
AS PARTITION pf_EncounterDate
ALL TO ([Primary]);
```

**Benefit:** Partition elimination reduces data scanned by **90%+** for date-range queries.

### 2. Columnstore Indexes
- Ideal for analytical queries (aggregates, scans)
- Compresses data 10x, fits more in memory
- Perfect for "last 30 days" type queries on encounters

### 3. Filtered Indexes
```sql
CREATE INDEX IX_Encounters_Active 
ON Encounters(EncounterDate) 
WHERE Status = 'Active';
```

**Verdict:** 💡 For NHS SQL Server, partitioning + columnstore = major performance gains on large tables.

---

## 🔧 Open Source BI Alternatives (2026 Update)

| Tool | Best For | NHS Fit |
|------|----------|---------|
| **Apache Superset** | SQL teams, embedded analytics | ⭐⭐⭐ |
| **Metabase** | Self-service, non-technical users | ⭐⭐⭐ |
| **Looker Studio** | Free, Google ecosystem | ⭐⭐ |
| **Evidence** | Markdown + SQL reports | ⭐⭐⭐ |
| **Retable** | No-code, collaborative | ⭐⭐ |

**Top picks for NHS:**
1. **Metabase** — easiest for non-technical staff, free tier works
2. **Apache Superset** — if you need SQL-heavy, embeddable
3. **Evidence** — if you want version-controlled static reports

---

## 📈 Report Automation: Python + Scheduler

**2026 stack for NHS automated reports:**

| Component | Tool |
|-----------|------|
| Data processing | pandas / polars |
| SQL queries | SQLAlchemy |
| Excel output | openpyxl / xlsxwriter |
| Charts | matplotlib / plotly |
| Scheduling | APScheduler / cron |
| Email | yagmail / smtplib |
| PDF generation | WeasyPrint / pdfkit |

**Example NHS weekly report pipeline:**
```python
from apscheduler.schedulers.blocking import BlockingScheduler
import pandas as pd
from sqlalchemy import create_engine
import yagmail

def generate_weekly_report():
    # 1. Pull data
    df = pd.read_sql("SELECT * FROM waiting_times WHERE week = current_week", engine)
    
    # 2. Generate Excel with charts
    with pd.ExcelWriter('weekly_summary.xlsx') as writer:
        df.to_excel(writer, sheet_name='Data')
        # Add pivot, charts...
    
    # 3. Email
    yagmail.send('team@nhs.gov', 'Weekly Report', 'See attached', 'weekly_summary.xlsx')

scheduler = BlockingScheduler()
scheduler.add_job(generate_weekly_report, 'cron', day_of_week='fri', hour=17)
scheduler.start()
```

---

## 🛠 Tools Worth Exploring

- **PawSQL** — intelligent query optimization for MySQL/PostgreSQL
- **Great Expectations** — data quality validation (covered before, still relevant)
- **DBT** — data transformation in warehouse, popular in healthcare analytics
- **MindsDB** — AI-powered database, interesting for predictive analytics

---

## Summary for John

**Priority try list:**
1. **Polars** — test on a sample NHS dataset, compare to pandas
2. **ydata-profiling** — run on new data imports for quick quality checks
3. **SQL partitioning** — discuss with DB admin for large encounter tables
4. **Evidence** — if you want Markdown-based static reports in git

**Next steps:**
- Benchmark Polars vs pandas on sample NHS waiting times data
- Try ydata-profiling on any new dataset import
- Ask about SQL Server partitioning strategy for main tables

---

*Discovered: 2026-03-05 10:00 UTC*
*Source: Web search on Python data analysis, Power BI alternatives, SQL optimization, healthcare analytics*
