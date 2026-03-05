# Discovery — March 5, 2026 — 1200 UTC

## Relevant to: John's NHS analyst workflow (Python, Power BI alternatives, SQL, report automation)

---

## 🔥 Top Discovery: NHS Python Community (nhs-pycom.net)

**What:** Official community championing Python in NHS and healthcare - the go-to resource for NHS analysts.

**Why it's interesting:**
- Free resources, tutorials, and packages specifically for NHS data
- **NHS Reproducible Analytical Pipeline (RAP)** - automated reporting standards used by NHS England
- Collaborative projects with Google Health
- Active community of practice

**Resources found:**
- [nhs-pycom.net](https://nhs-pycom.net) - main community site
- [NHS GitHub topics](https://github.com/topics/nhs) - open source NHS projects
- [NHSDigital/data-analytics-services](https://github.com/NHSDigital/data-analytics-services) - official NHS Analytics open source

**For John's workflow:**
- Could adopt RAP principles for automated NHS reports
- Pre-built packages for common NHS data issues (hospital episode overlaps, waiting times)

**Verdict:** 💡 Essential bookmark. This is THE community for NHS analysts using Python.

---

## 🏥 NHS Time of Travel & SPC Charts

**What:** NHS Python projects for healthcare analytics - process behavior charts that automatically detect signals of change.

**Why interesting:**
- Statistical Process Control (SPC) charts built specifically for NHS data
- Automatically detects signals of process change
- Updates charts automatically as new data arrives
- Google Health + NHS Python Community collaboration

**Project:** [nhs_time_of_travel](https://github.com/nhsx/nhs_time_of_travel)

**For John's workflow:**
- Perfect for monitoring KPIs like waiting times, bed occupancy, A&E targets
- Automates the "is this a real change or just noise?" analysis

**Verdict:** 💡 Directly applicable to John's NHS reporting work.

---

## 📊 Power BI Alternatives: Superset vs Metabase

**What:** Two leading open-source BI tools as Power BI replacements.

**Apache Superset:**
- Enterprise-grade, used by Airbnb, Netflix
- SQL Lab for query building
- Extensive database support (PostgreSQL, MySQL, BigQuery, Snowflake, Druid)
- Rich visualization builder
- Best for: teams with data engineering support

**Metabase:**
- More beginner-friendly
- Question-builder UI (no SQL required)
- Embeddable dashboards
- Self-host or cloud options
- Best for: quick ad-hoc analysis, sharing with non-technical users

**For John's workflow:**
- Either could replace Power BI
- Superset = more power, steeper learning curve
- Metabase = faster time-to-value, simpler

**Verdict:** 💡 Metabase likely better for NHS analyst workflow (faster setup, easier for stakeholders).

---

## 🐘 PostgreSQL Query Optimization Resources

**What:** Current best practices for SQL performance tuning.

**Key techniques found:**
1. **EXPLAIN ANALYZE** - actual vs estimated rows, timing, cache hits
2. **pg_stat_statements** - find slowest queries across all executions
3. **Indexing strategies** - B-tree for equality, GIN for full-text/JSON
4. **Partitioning** - split large tables by date (common for NHS data)
5. **Proper data types** - avoid VARCHAR where CHAR/INT works

**Resources:**
- [PostgreSQL Performance Tips](https://www.postgresql.org/docs/current/performance-tips.html) - official docs
- [Haki Benita: Unconventional PostgreSQL Optimizations](https://hakibenita.com/postgresql-unconventional-optimizations) - advanced techniques
- [Tiger Data: Query Optimization Best Practices](https://www.tigerdata.com/blog/best-practices-for-query-optimization-in-postgresql)

**For John's workflow:**
- Relevant if NHS data in PostgreSQL
- EXPLAIN ANALYZE essential for understanding query plans
- Partitioning by month/quarter useful for large historical datasets

**Verdict:** 📌 Worth exploring if John deals with slow NHS SQL queries.

---

## 📋 Reproducible Analytical Pipelines (RAP)

**What:** NHS England's standard for automated, reproducible reporting.

**Principles:**
- Code over spreadsheets
- Version control
- Automated data pipelines
- Documentation as code

**Implementation:**
- Python-based
- GitHub Actions for automation
- Outputs: HTML reports, PDFs, dashboards

**For John's workflow:**
- Directly applicable to his report automation goals
- Could replace manual Excel/Power BI refreshes

**Resource:** [NHS RAP GitHub](https://github.com/nhsengland) - Friends and Family Test automation example

**Verdict:** 💡 This is exactly what John should aim for in his Python automation journey.

---

## Summary for John

| Category | Discovery | Priority |
|----------|-----------|----------|
| Community | NHS Python Community | ⭐⭐⭐ |
| BI Tool | Metabase (simpler) or Superset (power) | ⭐⭐⭐ |
| SQL | EXPLAIN ANALYZE + pg_stat_statements | ⭐⭐ |
| Automation | Reproducible Analytical Pipelines (RAP) | ⭐⭐⭐ |
| Visualization | NHS SPC charts (process monitoring) | ⭐⭐ |

**Next steps suggested:**
1. Bookmark nhs-pycom.net and explore RAP resources
2. Try Metabase - simpler to set up than Superset
3. Review slow NHS queries with EXPLAIN ANALYZE

---

*Discovery cycle: 2026-03-05 1200 UTC*
