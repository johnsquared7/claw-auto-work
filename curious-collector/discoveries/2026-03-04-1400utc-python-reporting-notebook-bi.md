# Discovery: Python Reporting & Notebook-Based BI for NHS Workflow
**Date:** 2026-03-04 14:00 UTC | **Source:** Autonomous Discovery Cycle

---

## 🔑 Key Finding: Evidence.dev — Notebook-First BI as Code

**URL:** https://github.com/evidence-dev/evidence

Evidence is an open-source alternative to drag-and-drop BI tools (like Power BI). It generates a static website from markdown files containing SQL queries.

**How it works:**
- Write SQL queries inside markdown files
- Charts and components render from query results
- Supports templated pages, loops, and conditional logic
- VSCode extension available for live preview

**Why it's interesting for John:**
- **Version control** — Reports live in Git, not .pbix files
- **SQL-first** — Already heavy SQL user; stays in comfort zone
- **No drag-drop** — Code-based, reproducible reports
- **Self-hostable** — Deploy to Netlify/Vercel or internal infra

**Alternative to:** Power BI published reports, Excel-linked workbooks

**Getting started:**
```bash
# VSCode extension: "Evidence"
# Or CLI: npx create-evidence@latest
```

---

## 📄 Python PDF Report Automation Stack

**Stack:** Pandas + Jinja2 + WeasyPrint

For automated NHS reports that need PDF output, this is a proven pattern:

### 1. Pandas — Data Processing
- Load data from SQL, Excel, CSV
- Transform and aggregate for reports

### 2. Jinja2 — Templating
- HTML templates with dynamic data injection
- Loops, conditionals, reusable components

### 3. WeasyPrint — PDF Generation
- Convert HTML/CSS to PDF
- Full CSS support, page headers/footers

**Reference:** https://pbpython.com/pdf-reports.html

**Why it matters:** NHS often requires PDF-formatted reports for governance. This stack replaces manual Excel→PDF workflows with fully automated scripts.

---

## ⚡ Prefect — Simpler ETL for Report Automation

**URL:** https://www.prefect.io/

If Airflow feels overkill, Prefect is a modern Python-native orchestration tool:

- **Python-first** — Define pipelines in pure Python
- **Lightweight** — Can run locally or cloud-hosted
- **Scheduling** — Cron-style or event-based triggers
- **Dashboard** — Visualize pipeline runs and failures

**Use case:** Scheduled nightly extracts from NHS SQL Server → transform → upload to reporting database → trigger Evidence.dev rebuild

**Comparison:**
| Tool | Best For | Complexity |
|------|----------|------------|
| Prefect | Small-medium pipelines | Low |
| Airflow | Enterprise data platforms | High |
| Dagster | Data assets + lineage | Medium |

---

## 📊 Streamlit 1.23+ for Healthcare Dashboards

**What's new in 2026:**
- Real-time data streaming support
- Multi-threaded execution
- Enhanced session state management

**Healthcare use cases:**
- Interactive ward performance dashboards
- Patient flow analytics
- Waiting list visualizations
- Census data explorers

**Why Streamlit over Power BI:**
- Full Python control
- Custom logic possible
- Embeddable in other apps
- Free and open source

**ExampleNHS dashboard structure:**
```python
import streamlit as st
import pandas as pd
import plotly.express as px

st.title("NHS Trust Performance")
df = pd.read_sql("SELECT * FROM waits", conn)
fig = px.bar(df, x="Specialty", y="WaitList")
st.plotly_chart(fig)
```

---

## 🎯 Relevance to John's NHS Workflow

| Current Pain | Discovery |
|--------------|-----------|
| Power BI file management | Evidence.dev (Git-based, SQL-first) |
| Manual PDF exports | Pandas + Jinja + WeasyPrint |
| Scheduled report runs | Prefect (Python-native scheduling) |
| Interactive dashboards | Streamlit 1.23+ (real-time support) |

---

## 🔭 Next Steps for Exploration

1. **Try Evidence.dev** with a sample NHS dataset
2. **Build PDF template** using Jinja2 + WeasyPrint for one monthly report
3. **Evaluate Prefect** for a simple nightly extract

---

*Discovery completed 2026-03-04 14:00 UTC*
