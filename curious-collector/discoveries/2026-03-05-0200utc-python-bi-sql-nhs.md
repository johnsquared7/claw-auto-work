# Discovery: Python Data Tools & Open Source BI for NHS Analysts
**Date:** 2026-03-05 02:00 UTC | **Source:** Autonomous Discovery Cycle

---

## 🔑 Key Finding: cuDF — GPU-Accelerated Dataframes

**URL:** https://github.com/rapidsai/cudf

NVIDIA's cuDF provides GPU-accelerated DataFrame operations with a pandas-like API. For NHS analysts working with large datasets, this can provide **10-100x speedups** over CPU-based pandas.

**Why it's interesting:**
- Drop-in replacement for pandas operations
- Works with NVMe SSDs for larger-than-GPU-memory datasets
- Integrates with RAPIDS ecosystem (cuML for ML)

**NHS use case:** Processing massive waiting list extracts, SUS data, or any dataset that currently takes minutes/hours in pandas.

```python
import cudf

# Same API as pandas but GPU-accelerated
df = cudf.read_csv("large_dataset.csv")
result = df.groupby("specialty").agg({"wait_weeks": "mean"})
```

**Note:** Requires NVIDIA GPU. For NHS trusts without GPU hardware, Polars (CPU-optimized) is still the best choice.

---

## 📊 Lightdash — dbt-Powered Open Source BI

**URL:** https://lightdash.com/

Lightdash is an open-source BI tool that integrates directly with dbt (data build tool). It's gained significant traction in 2025-2026.

**Why it stands out:**
- **dbt-native** — All your dbt models become instant dashboards
- **Self-hosted** — Full control, no licensing costs
- **Semantic layer** — Defined metrics in code, not UI
- **Shareable** — Embeddable charts, Slack integrations

**Comparison with Power BI:**
| Feature | Power BI | Lightdash |
|---------|----------|-----------|
| Cost | Per-user license | Free (open source) |
| Setup | Manual建模 | Code-first (dbt) |
| Data model | UI-based | YAML/code-based |
| Embedding | Limited | Full |

**NHS fit:** If your team uses dbt (or is considering it), Lightdash removes the need for separate BI tooling. Good for analyst teams who want version-controlled metrics.

---

## 🖥️ Apache Superset — Enterprise-Grade Open Source BI

**URL:** https://superset.apache.org/

Apache Superset is a modern, enterprise-ready BI platform that's matured significantly.

**Strengths:**
- **Visual SQL query builder** — No SQL required for basic charts
- **SQL Lab** — Direct SQL for analysts who want it
- **Native SQL support** — Connects to PostgreSQL, MySQL, SQL Server, BigQuery, Snowflake, etc.
- **Dashboards** — Rich, interactive, embeddable
- **Row-level security** — Important for NHS data

**Self-hosting requirement:** Needs Docker/Kubernetes or a VM. Not a SaaS (contrast with Looker Studio).

**NHS consideration:** Superset is ideal for trusts with in-house data teams who can manage the infrastructure. Steeper setup than Metabase but more powerful.

---

## 🐦 Metabase — The Friendly Open Source Query Tool

**URL:** https://www.metabase.com/

Metabase is the "easy mode" of open source BI. Great for teams that want quick answers without heavy setup.

**Why it's popular:**
- **Zero-setup** — Download, run, start querying
- **Question builder** — Point-and-click SQL generation
- **Native SQL mode** — For analysts who want control
- **Embedding** — Put dashboards in other apps
- **Slack/Email alerts** — Automated report delivery

**Comparison:**
| Tool | Best For | Setup Effort |
|------|----------|--------------|
| Metabase | Quick insights, non-technical users | Low |
| Superset | Enterprise, custom viz | Medium |
| Lightdash | dbt-powered teams | Medium |
| Power BI | Full Microsoft ecosystem | Low |

---

## 📈 SQL Query Optimization Tools (2026)

### Recommended Tools for DBAs and Analysts

**1. SolarWinds Database Performance Analyzer**
- SQL Server, Oracle, MySQL, PostgreSQL support
- Query-level analysis and recommendations
- **URL:** https://www.solarwinds.com/database-performance-analyzer

**2. SentryOne (now part of SolarWinds)**
- Index analysis, missing index suggestions
- Execution plan visualization

**3. Redgate SQL Monitor**
- Real-time alerting
- Wait statistics analysis

**4. dbForge Studio (Devart)**
- Visual query profiler
- Index maintenance recommendations

### Free/Open Source Options

**5. pg_stat_statements (PostgreSQL)**
- Built-in query performance analysis
- Tracks execution time, I/O, cache hits

**6. sp_BlitzIndex (SQL Server)**
- Free script from Brent Ozar
- Analyzes indexes, recommends improvements
- **URL:** https://www.brentozar.com/blitzindex/

---

## 🏥 NHS-Specific SQL Patterns

For NHS analysts working with SQL Server, key optimization patterns:

```sql
-- Covered index example (includes SELECT columns)
CREATE NONCLUSTERED INDEX IX_WaitList_Specialty 
ON WaitingList(Specialty, Status) 
INCLUDE (PatientID, WaitWeeks, TreatmentDate);

-- Filtered index (for common WHERE clause)
CREATE NONCLUSTERED INDEX IX_WaitList_Active 
ON WaitingList(Status) 
WHERE Status = 'Waiting';
```

**Common NHS performance issues:**
- Missing indexes on date columns (common in temporal data)
- Functions on indexed columns (e.g., `WHERE YEAR(AdmissionDate) = 2025`)
- UDTs (User-Defined Tables) in procedures causing table scans

---

## 🔧 Report Automation with Python

### Tools Worth Exploring

**1. Great Expectations (covered previously)**
- Data quality validation in pipelines
- Automatic profiling and schema checks

**2. Papermill**
- Parameterized Jupyter notebooks
- Schedule notebook execution
- **URL:** https://papermill.readthedocs.io/

**3. Prefect / Dagster**
- Modern workflow orchestration
- **Prefect:** https://www.prefect.io/
- **Dagster:** https://dagster.io/

**4. Schedule library**
- Simple Python cron replacement
- **URL:** https://schedule.readthedocs.io/

### Example: Automated Weekly Report

```python
import schedule
import time

def generate_weekly_report():
    # 1. Pull data from SQL Server
    df = pull_waiting_list_data()
    
    # 2. Process with Polars (faster than pandas)
    summary = process_with_polars(df)
    
    # 3. Generate HTML report
    html = render_template(summary)
    
    # 4. Email to stakeholders
    send_email(html)

schedule.every().monday.at("07:00").do(generate_weekly_report)
```

---

## 📊 Decision Matrix for John's NHS Workflow

| Pain Point | Recommendation | Priority |
|------------|----------------|----------|
| Slow large data processing | Polars (immediate) | High |
| Need GPU acceleration | cuDF (if GPU available) | Medium |
| Power BI licensing | Lightdash/Metabase (explore) | Medium |
| Report automation | Prefect + Polars | High |
| SQL performance | Use sp_BlitzIndex / DPA | High |

---

## 🎯 Relevance to John's NHS Workflow

John is an NHS data analyst who likely:
- Uses SQL Server for patient/waiting list data
- Creates reports for management
- Deals with large datasets (Pandas struggles)
- May face Power BI licensing constraints

**Immediate wins:**
1. **Switch to Polars** — 3-10x faster, same syntax
2. **Try DuckDB** — For ad-hoc SQL analytics without a DB server
3. **Explore Metabase** — If Power BI costs are an issue

---

## 🔭 Next Steps

1. **Test Polars** on actual NHS dataset — benchmark against current pandas
2. **Install DuckDB** — Try one SQL analysis without SQL Server
3. **Spin up Metabase** — Test with a sample dataset
4. **Review execution plans** — Use sp_BlitzIndex on production queries

---

*Discovery completed 2026-03-05 02:00 UTC*
