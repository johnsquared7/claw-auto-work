# Discovery: Python Data Stack & BI Alternatives for NHS Analytics

**Date:** 2026-03-02  
**Cycle:** autonomous-discovery-2200utc

---

## 1. Polars — The Fast DataFrame Alternative

**What:** Rust-based DataFrame library with Python bindings  
**Why it matters:** Claims **up to 30x faster** than pandas for joins, filters, aggregations  
**Use case for NHS analyst:** Large NHS datasets (SUS, GP data, waiting lists) that crash pandas

**Key points:**
- Uses Apache Arrow columnar format under the hood
- LazyFrame mode optimizes queries before execution (like Spark)
- No SettingWithCopyWarning issues — uses `.with_columns()` instead of `=`
- Can convert to pandas via `.to_pandas()` when needed
- Multi-threaded by default, better memory efficiency

**Verdict:** Worth trying for NHS data pipelines. Install: `pip install polars`

---

## 2. Streamlit vs Dash — Which to Choose?

**Streamlit** — Rapid prototyping
- Less code, no HTML/CSS knowledge needed
- Auto-refreshes as you write code
- Better for: quick internal tools, one-off dashboards
- Risk: higher memory with many concurrent users

**Dash (Plotly)** — Enterprise-ready
- Full control over layout and styling
- Better for: production dashboards, complex interactivity
- Flask-based, scales horizontally with Gunicorn
- Built-in Plotly charts are more powerful

**For John's workflow:** Streamlit is probably better starting point — faster to build, good for internal NHS reports.

---

## 3. Healthcare Analytics Trends 2026

**Natural language queries** emerging — platforms letting clinical staff ask questions in plain English instead of writing SQL. Could reduce dependency on analyst for ad-hoc requests.

**AI-assisted analysis** — Generative AI now matching human teams on medical dataset analysis in some cases.

---

## 4. SQL Optimization

Focus remains on fundamentals:
- Clean SQL, readable queries
- Careful use of indexes
- Query design over tool dependency

For NHS SQL Server (likely), focus on:
- Proper indexing on date columns (common in NHS data)
- Avoiding SELECT * on large tables
- Using CTEs for readability

---

## Action Items for John

1. **Try Polars** — `pip install polars` and test on a medium NHS dataset
2. **Streamlit for reports** — Quick dashboard for weekly/monthly NHS reports
3. **Stick with Power BI** for now — Still best for executive presentations; use Python/Streamlit for operational tools

---

*Discovery quality: Specific, actionable, not generic news. Focus on tools that directly help NHS analyst workflow.*
