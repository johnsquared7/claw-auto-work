# Discovery — March 6th, 2026 — 16:00 UTC

**Theme:** SQL Optimization, Report Automation & Python EDA Tools

---

## 🎯 Key Finds

### 1. YData Profiling (formerly Pandas Profiling)
**URL:** https://github.com/ydataai/ydata-profiling

Automated exploratory data analysis. Generates interactive HTML reports with distributions, correlations, missing values, and text analysis. Successor to pandas-profiling with better performance and features.

**Why it's interesting:** Zero-effort EDA for NHS datasets. Quickly understand data quality issues before analysis.

---

### 2. dbForge AI Assistant for SQL
**URL:** https://www.devart.com/dbforge/ai-assistant/

AI-powered SQL optimization and generation. Analyzes queries, suggests index improvements, explains execution plans, and generates SQL from natural language. Supports SQL Server, MySQL, PostgreSQL, Oracle.

**Why it's interesting:** Practical AI helper for query tuning without needing Copilot subscriptions.

---

### 3. SSMS Query Hint Recommendation Tool (New in SSMS 22)
**URL:** https://www.mssqltips.com/sqlservertip/11617/ssms-query-hint-recommendation-tool/

SQL Server Management Studio 22 now includes a query hint recommendation feature. Analyzes your queries and suggests optimization hints like OPTIMIZE FOR, RECOMPILE, or index hints.

**Why it's relevant:** If John's using SQL Server, this native tool could improve query performance without third-party tools.

---

### 4. GitHub Copilot in SSMS and VS Code
**URL:** https://blog.fabric.microsoft.com/en-US/blog/no-more-excuses-ai-powered-assistants-are-in-ssms-vs-code-and-fabric/

Microsoft now integrates Copilot into SSMS. Get AI chat, code actions, and query optimization directly in the tool. Works with Fabric SQL databases but also applicable to standard SQL Server.

**Why it's relevant:** Free with Microsoft accounts. Could replace manual query tuning for SQL Server users.

---

### 5. Looker Studio (formerly Data Studio)
**URL:** https://lookerstudio.google.com/

Free Google BI tool. Connect to Google Sheets, BigQuery, PostgreSQL, MySQL, or 100+ data sources. Interactive dashboards, automatic sharing, embeddable reports.

**Why it's relevant:** Free alternative to Power BI. Better Google integration. Worth evaluating if cost is a factor.

---

### 6. Metabase — Open Source Query Tool
**URL://https://metabase.com/

Simple SQL question builder + dashboards. Non-technical users can explore data safely (row-level permissions). Embedded analytics option. Self-hostable.

**Why it's relevant:** Easier than Superset for NHS teams who want self-service without full BI platform overhead.

---

### 7. Heidi Health — NHS-Compliant Document Generation
**URL:** https://www.heidihealth.com/

AI-powered clinical documentation. Generates NHS letters, reports, and documents from clinical encounters. NHS compliant, used by UK GP partnerships.

**Why it's relevant:** If John needs to generate formatted NHS documents/letters programmatically, this could replace manual Word mail merges.

---

### 8. docxtpl — Python Word Templating
**URL:** https://docxtpl.readthedocs.io/

Python library for filling Microsoft Word templates. Use Jinja2-style placeholders in .docx files, feed data from Python, generate formatted reports.

**Why it's relevant:** Perfect for automated NHS reports. Template stays in Word, data fills in automatically. No HTML conversion needed.

---

### 9. DuckDB — In-Memory Analytical Database
**URL:** https://duckdb.org/

Embedded SQL database like SQLite but analytical (columnar). Run SQL queries directly on CSV, Parquet files. No server needed. Python integration via `duckdb` package.

**Why it's relevant:** Instant local analytics. Query GBs of NHS data without setting up a database server. Great for ad-hoc analysis.

---

## 📊 Relevance to John's Workflow

| Need | Best Fit |
|------|----------|
| Quick data exploration | YData Profiling |
| SQL Server optimization | SSMS 22 hints, Copilot in SSMS |
| Free Power BI alternative | Looker Studio |
| Self-service NHS queries | Metabase |
| Word report automation | docxtpl |
| Ad-hoc data analysis | DuckDB |
| NHS document generation | Heidi Health |

---

## 💡 Recommendations

1. **Try YData Profiling** on a sample NHS dataset — instant data quality report
2. **Test SSMS 22** if on SQL Server — new hint recommendations could help slow queries
3. **Explore DuckDB** for one-off analyses — skip loading data into pandas
4. **Consider docxtpl** for any Word-based report automation

---

## 📚 Additional Notes

DuckDB + Polars + YData Profiling form a modern Python stack:
- DuckDB for SQL queries on files
- Polars for data transformation  
- YData Profiling for EDA
- docxtpl for Word output

This avoids heavy database infrastructure for exploratory work.

---

*Discovery cycle: 2026-03-06 16:00 UTC*