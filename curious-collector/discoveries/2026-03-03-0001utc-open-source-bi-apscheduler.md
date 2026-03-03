# Discovery: Open Source BI Tools & Python Scheduling for NHS Reports

**Date:** 2026-03-03  
**Cycle:** autonomous-discovery-0001utc

---

## 1. Evidence.dev — Code-First BI Alternative

**What:** Open-source framework for building data products using SQL and markdown  
**Why it matters:** Bridges the gap between analyst and developer — write SQL queries that render as interactive reports  
**Use case for NHS:** Automated monthly/weekly reports that are version-controlled and reproducible

**Key points:**
- Write SQL in markdown files → gets compiled into a static site with interactive data
- Every chart/dashboard is defined in code (no drag-and-drop)
- Supports dbt integration out of the box
- Great for: analyst teams who want reproducible, audit-ready reports
- Not great for: non-technical users who need ad-hoc exploration

**Verdict:** Worth trying if John wants to move toward "documentation-as-code" for NHS reports. Could replace some manual report generation.

**Link:** https://github.com/evidence-dev/evidence

---

## 2. Open Source BI Tools Comparison

| Tool | Best For | NHS Fit |
|------|----------|---------|
| **Metabase** | Non-technical users, quick dashboards | ⭐ Good — easy UI, no-code queries |
| **Superset** | Enterprise scale, advanced analytics | Good if you have dev resources |
| **Lightdash** | dbt-native teams | Less relevant unless using dbt |
| **Evidence** | Code-driven, version-controlled reports | ⭐ Good for reproducible analytics |

**Metabase** stands out for NHS — it has a **free open-source version** you can self-host, and the query builder is intuitive enough for clinical staff to use after basic training.

**Superset** is powerful but has a steeper learning curve — better for analysts who already know SQL well.

---

## 3. APScheduler for NHS Report Automation

**What:** Python job scheduling library  
**Why it matters:** Simple way to run Python scripts on a schedule (daily, weekly, cron-style) without external tools

**Use case:** Automated NHS report generation — run a Python script every Monday morning that pulls data, generates an Excel report, and emails it.

**Key points:**
- Three ways to schedule: interval, cron-like, fixed date/time
- Can run in-process (simple) or as a background service
- Supports persistent job stores (SQLAlchemy, Redis, MongoDB)
- Works on Windows — important for many NHS environments

**Example for NHS weekly report:**
```python
from apscheduler.schedulers.blocking import BlockingScheduler
from generate_nhs_report import create_weekly_report

scheduler = BlockingScheduler()
scheduler.add_job(create_weekly_report, 'cron', day_of_week='mon', hour=7)
scheduler.start()
```

**Alternative:** If just needs simple scheduling, Windows Task Scheduler + Python script works fine. APScheduler is better when you want the scheduling logic inside Python.

---

## 4. NHS Digital Open-Source Analytics

**What:** [NHSDigital/data-analytics-services](https://github.com/NHSDigital/data-analytics-services)  
**Why it matters:** Official NHS Digital team sharing open-source analytics tools and research

**Interesting projects:**
- Python packages for NHS data analysis
- Synthetic data research (useful for testing without using real patient data)
- LIME applications for healthcare image classification
- Research on AI/ML for NHS use cases

**Verdict:** Worth watching — these are official NHS tools that might align with John's workflow.

---

## 5. Quick Wins for John's Workflow

| Priority | Action | Effort |
|----------|--------|--------|
| 1 | Try APScheduler for one weekly report | Low |
| 2 | Explore Metabase for self-service NHS dashboards | Medium |
| 3 | Check out Evidence.dev for code-driven reports | Medium |
| 4 | Bookmark NHSDigital GitHub for future reference | Low |

---

## Quality Note

This discovery focuses on actionable tools, not generic news. All recommendations are relevant to an NHS analyst who uses Power BI, SQL, and is learning Python for automation.

---

*Cycle completed: 2026-03-03 00:01 UTC*
