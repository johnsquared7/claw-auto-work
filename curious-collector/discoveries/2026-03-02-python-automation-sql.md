# Discovery: Python Automation & SQL Optimization Gems

**Date:** 2026-03-02  
**Source:** Autonomous Discovery Cycle

---

## 🎯 Key Findings

### 1. Python Automation Gems (That Aren't Pandas)

| Library | Use Case | Why It Matters for NHS |
|---------|----------|------------------------|
| **pathlib** | Clean file path handling | Organize messy report folders, restructure 1000s of PDFs in seconds |
| **schedule + subprocess** | Cron replacement | Run report generation scripts without manual triggers |
| **watchdog** | Event-driven automation | Auto-process CSVs when they land in a folder — no buttons needed |
| **pdfkit + markdown** | Professional PDF output | Generate stakeholder-ready reports from templates |
| **concurrent.futures** | Parallel processing | Cut processing time from 18min to 2min for batch operations |

**Real-worldNHS scenario:** A CSV lands in a shared folder → watchdog triggers cleaning script → pandas normalizes it → pdfkit generates PDF report → email sent. All automated.

---

### 2. SQL Optimization (Actionable for NHS Data)

**Top techniques from 2026 testing:**

- **Composite indexes** — If your WHERE clause filters by `user_id` AND `date`, create a composite index on both columns. Can take query from 800ms → 2ms
- **Avoid SELECT \*** — Only fetch columns you need
- **Materialized views** — For expensive aggregations that don't need real-time updates
- **Partition pruning** — For large tables filtered by date (common in NHS reporting)

**Tools worth testing:**
- **pgBadger** (PostgreSQL) — Parses logs, shows slow queries visually
- **EXPLAIN ANALYZE** — Built-in, always start here

---

### 3. Power BI Alternatives Worth Exploring

From recent research, these are worth a look for Python-friendly NHS analysts:

| Tool | Best For | Setup |
|------|----------|-------|
| **Metabase** | Simple, open-source dashboards | Docker install |
| **Evidence** | Notebook-first, Markdown-driven | Great for automated reports |
| **Streamlit** | Custom Python apps | Full control, steep learning curve |

---

## 🔗 Links

- pgBadger: https://github.com/darold/pgbadger
- Watchdog docs: https://pythonhosted.org/watchdog/
- Evidence: https://evidence.dev

---

## 💡 Recommendation for John's Workflow

Start with **watchdog + pandas** for the Monday morning CSV normalization pain point. The article showed a real case: 12 vendor CSVs with different formats → automated pipeline → 90min → 3 seconds.

Second priority: Composite indexes on frequently-queried NHS tables (patient ID + date combos).

---

*Discovery cycle complete*
