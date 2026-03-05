# Discovery: AI SQL Optimization & Code-Based BI — March 2026

**Date:** 2026-03-05 20:00 UTC  
**Category:** SQL Optimization / Modern BI / Report Automation  
**Quality:** High — practical tools with immediate NHS workflow relevance

---

## TL;DR

4 discoveries for John's NHS analyst workflow:
1. **EverSQL** — AI-powered SQL query optimization for PostgreSQL/MySQL
2. **Evidence.dev** — SQL + Markdown reporting (BI as code)
3. **Lightdash** — dbt-native BI with AI assistant
4. **AI SQL Optimization Trend 2026** — Key patterns from enterprise research

---

## 1. EverSQL — AI-Powered SQL Optimization

**Website:** https://www.eversql.com/  
**What:** AI-based tool that automatically rewrites and indexes SQL queries for PostgreSQL and MySQL

**Why it matters for NHS:**
- **Automatic query rewriting** — paste a slow query, get optimized version
- **Index recommendations** — tells you exactly which indexes to create
- **Non-intrusive sensor** — monitors database performance ongoing
- **Cost reduction** — identifies redundant indexes, unused tables

**How it works:**
1. Submit a SQL query for optimization
2. EverSQL analyzes and returns optimized version
3. Install optional performance sensor for ongoing monitoring
4. Get recommendations for indexes and schema changes

**Key feature:** Explains *why* each optimization was made — not a black box.

**Pricing:** Free tier available; paid for advanced features

**Use case for John:** Have a slow Power BI dataset refresh? Paste the underlying SQL query into EverSQL for instant optimization suggestions.

---

## 2. Evidence.dev — Business Intelligence as Code

**Website:** https://evidence.dev/  
**What:** Build reports using SQL + Markdown with automatic visualizations

**Why it matters for NHS:**
- **Git-friendly** — reports are code, can be version controlled
- **SQL-first** — write queries, Evidence auto-generates charts
- **Markdown simplicity** — structure reports with familiar syntax
- **Self-hosted** — deploy on NHS infrastructure
- **AI-enhanced IDE** — autocomplete, error checking, AI debugging

**Example syntax:**
```markdown
# Monthly Waiting List Report

## Overview
Total patients waiting: {value}

<BigValue
  data={waiting_list_summary}
  value=count_patients
/>

## By Trust
<BarChart
  data={trust_data}
  x=trust_name
  y=waiting_count
/>
```

**The killer feature:** Automatic visualization selection — Evidence picks the best chart type based on your data.

**vs Power BI:**
| Aspect | Power BI | Evidence |
|--------|----------|----------|
| Version control | Difficult | Native Git |
| SQL editing | Basic | Full IDE |
| Self-host | No | Yes |
| Learning curve | Medium | Low (if you know SQL) |
| Licensing | Per-user | Open source |

**Best for:** NHS teams who want reports version-controlled alongside their SQL queries.

---

## 3. Lightdash — AI-Native dbt BI Platform

**Website:** https://www.lightdash.com/  
**What:** Open-source BI that integrates directly with dbt models

**Why it matters for NHS:**
- **dbt integration** — your dbt models become explorable tables automatically
- **AI-native** — natural language queries, AI builds dashboards
- **Self-serve analytics** — non-technical users create charts without SQL
- **Unlimited users** — no per-seat licensing like Looker/Power BI
- **HIPAA compliant** — relevant for healthcare data

**Key differentiator:** If John's team uses dbt for data transformation, Lightdash turns those models into dashboards automatically. No duplicate metric definitions.

**Features:**
- Metrics layer — define KPIs once, use everywhere
- AI assistant — describe what you want, AI builds the chart
- Git integration — dashboards version-controlled
- Space-level permissions — control who sees what

**Best for:** NHS teams already using or considering dbt for data transformation.

---

## 4. AI SQL Optimization Trends 2026

**Source:** Syncfusion Blog (June 2025 research summary)

**Key insights for NHS analysts:**

### Learned Query Optimization
- Modern SQL engines now learn from historical query patterns
- SQL Server 2025: Intelligent Query Processing with cardinality estimation feedback
- Oracle AI Database 26ai: In-database AI agents for dynamic tuning

### Adaptive Execution Plans
- Systems can switch between multiple plans based on runtime conditions
- SQL Server 2025: Optional Parameter Plan Optimization
- IBM Db2: ML-based tuning in recent releases

### Vector Indexes in SQL Databases
- SQL Server 2025: DiskANN-powered vector indexing
- Oracle 26ai: Native vector search support
- Enables semantic search directly in the database

### Practical Recommendations:
1. **Index redundancy detection** — modern tools identify duplicate/unused indexes
2. **Plan regression monitoring** — track when query plans go bad
3. **Workload-aware indexing** — AI recommends indexes based on actual usage patterns

**For John:** If NHS is on SQL Server, the 2025/2026 Intelligent Query Processing features could provide automatic performance gains without code changes.

---

## Comparison: When to Use Each Tool

| Tool | Best For | NHS Use Case |
|------|----------|--------------|
| **EverSQL** | Slow query debugging | Optimize Power BI refresh queries |
| **Evidence** | Report-as-code | Version-controlled monthly reports |
| **Lightdash** | dbt teams | Self-serve analytics on data warehouse |
| **Built-in AI** | SQL Server 2025 shops | Automatic query optimization |

---

## Priority Recommendation

| Priority | Tool | Why |
|----------|------|-----|
| 1 | **EverSQL** | Immediate value — paste slow query, get fix |
| 2 | **Evidence** | Try for a single report to test workflow |
| 3 | **Lightdash** | Only if using dbt |
| 4 | **SQL Server AI features** | Check if NHS is on SQL Server 2025 |

---

## Key Trend: BI as Code

The biggest insight from this research cycle:

> Modern BI is moving from "drag and drop dashboards" to "reports as code."

This matters because:
- **Version control** — track who changed what, when
- **Code review** — colleagues can review report changes
- **Reproducibility** — anyone can recreate the report from source
- **Collaboration** — same tools as software development

For NHS teams: Evidence.dev or dbt + Lightdash could replace manual Power BI report creation with a more maintainable, auditable workflow.

---

## Sources

- EverSQL: https://www.eversql.com/
- Evidence: https://evidence.dev/
- Lightdash: https://www.lightdash.com/
- Syncfusion Blog: "AI for SQL Performance: How AI is Transforming Query Optimization in 2026"
- OpenAlternative: "10 Best Open Source Power BI Alternatives in 2026"