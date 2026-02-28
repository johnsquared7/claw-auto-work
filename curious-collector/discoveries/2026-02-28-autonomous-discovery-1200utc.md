# Curious Collector — Autonomous Discovery Cycle

*Run time: 2026-02-28 12:00 UTC*  
*Focus: Python data analysis, Power BI alternatives, SQL optimization, report automation for NHS analyst workflows.*

---

## 1) Ibis (portable DataFrame API across 20+ backends)

**URLs**
- https://ibis-project.org/

**Why this is genuinely interesting**
- Same Python expression API can run on DuckDB/Polars locally, then on warehouse engines later with minimal code change.
- Explicit bridge between SQL-style analytics and Python dataframe workflows.

**NHS workflow angle**
- Lets John prototype fast on local extracts, then move identical logic to production SQL backends instead of rewriting analysis twice.

**Quick pilot**
- Rebuild one recurring pandas report using Ibis + DuckDB locally, then swap backend to current SQL engine and compare query parity.

---

## 2) pg_duckdb (DuckDB analytics engine embedded in PostgreSQL)

**URLs**
- https://github.com/duckdb/pg_duckdb
- https://motherduck.com/blog/pg-duckdb-release/

**Why this is genuinely interesting**
- Not another dashboard tool: this is execution-engine leverage.
- Can route analytical SQL inside Postgres to DuckDB’s vectorized engine (`duckdb.force_execution=true`) without rewriting the whole analytics stack.

**NHS workflow angle**
- Useful when operational data already lives in Postgres but analyst queries/report extracts are slow.
- Potential “speed layer” without immediate platform migration.

**Quick pilot**
- Benchmark one heavy monthly reporting query native Postgres vs pg_duckdb execution path.

---

## 3) PEV2 (Postgres EXPLAIN visualizer with zero-install local mode)

**URLs**
- https://github.com/dalibo/pev2
- https://raw.githubusercontent.com/dalibo/pev2/master/README.md
- https://explain.dalibo.com

**Why this is genuinely interesting**
- Directly converts ugly EXPLAIN plans into readable graph structure.
- Has offline/local HTML mode (`pev2.html`) for environments where installing tools is friction-heavy.

**NHS workflow angle**
- Fast way to debug slow SQL in analyst teams that don’t have deep DBA support.
- Better shared understanding during query optimization reviews.

**Quick pilot**
- Take top 3 slow report queries, export plans, review in PEV2, and log index/join-order fixes.

---

## 4) DuckDB spatial join operator gains (v1.3.0)

**URLs**
- https://duckdb.org/2025/08/08/spatial-joins.html
- https://motherduck.com/blog/duckdb-ecosystem-newsletter-september-2025/

**Why this is genuinely interesting**
- Dedicated `SPATIAL_JOIN` operator with reported major performance gains (up to 58x in cited benchmarks).
- Meaningful if geography is part of NHS reporting (ICB/place/PCN mapping, postcode or boundary joins).

**NHS workflow angle**
- Spatial enrichments (service usage by area, catchment overlays) can become practical in routine analyst workflows rather than one-off heavy jobs.

**Quick pilot**
- Re-run one existing area-based join workflow in DuckDB 1.3+ and compare runtime/cost vs current approach.

---

## 5) Quarto parameterization pattern for batch report packs

**URL**
- https://quarto.org/docs/computations/parameters.html

**Why this is genuinely interesting**
- Mature parameter model (Papermill-style for Python) enabling one template to render many audience/site/time-window variants.
- Strong fit for repeated static outputs where dashboard interactivity is overkill.

**NHS workflow angle**
- Replace repetitive “copy report, edit filters, export” work with scheduled parameterized batch rendering.

**Quick pilot**
- Generate one monthly report template and render for 3 org units automatically.

---

## Recommended next action (highest ROI)

**Start with #3 + #5 together:**
1. Use PEV2 to optimize one slow SQL extract.
2. Feed the optimized query into a parameterized Quarto report.

That pair gives immediate analyst time savings (faster query + automated delivery) without a big platform change.

---

*Collector note:* This cycle intentionally skipped generic “top 10 BI tools” lists and focused on leverage points that can improve SQL/reporting throughput in John’s existing NHS-style workflow.
