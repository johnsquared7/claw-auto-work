# Discovery — 2026-03-05 0400 UTC

**Focus:** Python Data Analysis, Power BI Alternatives, SQL Optimization, Report Automation

---

## 🐍 Python Data Analysis

### Polars — The pandas Replacement Gaining Momentum
- **What:** Rust-based DataFrame library, 10x faster than pandas
- **Why it matters:** Handles millions of rows effortlessly, simpler cleaner code
- **Use case for NHS:** Large dataset processing (waiting times, bed occupancy)
- **Source:** pola.rs, Real Python
- **Link:** https://pola.rs/

### DuckDB + Polars + Pandas Stack
- **Pattern emerging in 2026:** Use DuckDB for SQL-driven data prep, Polars for speed, pandas for ecosystem integration
- **Perfect for:** NHS analysts who need SQL but want Python performance
- **Source:** DEV Community
- **Link:** https://dev.to/dataformathub/python-data-processing-2026-deep-dive-into-pandas-polars-and-duckdb-2c1

---

## 📊 Power BI Alternatives

### Chat2DB — AI-Powered SQL Workbench
- **What:** End-to-end AI workflow combining text-to-SQL, intelligent optimization, visual analytics
- **Key feature:** Schema-aware query understanding + automatic SQL rewriting
- **Free tier:** Yes
- **Source:** index.dev
- **Link:** https://www.index.dev/blog/ai-tools-sql-generation-query-optimization

### Evidence — Markdown-First BI
- **Already in John's stack** — worth noting it's gaining traction
- **Why:** Write reports in Markdown, gets converted to interactive dashboards
- **Great for:** Version-controlled, reproducible NHS reports

---

## ⚡ SQL Optimization

### Key Tools for 2026
| Tool | Use Case | Platform |
|------|----------|----------|
| SolarWinds | Real-time query monitoring, DB health | Commercial |
| Visual Expert | Static analysis for PL/SQL, T-SQL | Commercial |
| pg_stat_statements | PostgreSQL query profiling | Open source |
| Query Store | SQL Server performance | Built-in |

### Healthcare-Specific SQL Patterns
- JOIN, CASE WHEN, CTE, RANK(), GROUP BY for hospital management analysis
- Source: Medium article on healthcare SQL-driven analysis
- **Link:** https://medium.com/@jayita_chatterjee/healthcare-management-optimization-a-comprehensive-sql-driven-analysis-45249910505f

---

## 🔄 Report Automation

### Python Excel Automation Stack
- **Libraries:** openpyxl, xlsxwriter, pandas, matplotlib, plotly
- **Pattern:** Query → Transform → Generate → Email
- **Scheduling:** schedule library or APScheduler
- **Source:** Plotly blog
- **Link:** https://plotly.com/blog/automate-excel-reports-with-python/

### NHS Automation Examples
- **Berkshire Healthcare NHS FT** — Using RPA robots for HR, Finance, Estates, Governance
- **What they automate:** Word, Excel, PDFs, Teams, clinical systems
- **Source:** Berkshire Healthcare IA team
- **Link:** https://ia.berkshirehealthcare.nhs.uk/

### FlowForma — NHS Process Automation
- No-code platform used by NHS trusts
- Document generation, workflow automation
- **Link:** https://www.flowforma.com/digital-transformation-nhs

---

## 💡 Recommendations for John

1. **Try Polars** — Replace pandas for large NHS datasets; keep pandas for ecosystem compatibility
2. **Explore Chat2DB** — Free AI SQL assistant could speed up query writing
3. **Consider Evidence** — If Power BI feels heavy, Markdown-first BI fits version-controlled workflows
4. **NHS RPA examples** — Berkshire Healthcare shows what's possible with automation

---

*Discovery cycle: 2026-03-05 0400 UTC*
*Focus: NHS analyst workflow (Python, SQL, BI, automation)*
