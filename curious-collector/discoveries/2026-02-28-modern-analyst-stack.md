# Discovery: The Modern Local Data Stack for NHS Analytics
## February 28, 2026

**Context:** Moving away from heavy, manual Power BI workflows to fast, code-first, reproducible local stacks.

### 1. The "Modern Local Data Stack" (DuckDB + dbt + Evidence.dev)
For an analyst frustrated by Power BI's "click-heavy" interface and slow refresh times, this open-source stack is a revelation.
- **DuckDB:** An in-process SQL OLAP database. It runs locally, reads Parquet/CSV/Excel instantly, and handles millions of rows in milliseconds without a server. It's "SQLite for Analytics."
- **dbt (Data Build Tool):** Manage your SQL transformations in version-controlled files, not hidden in Power Query steps.
- **Evidence.dev:** A Business Intelligence tool that runs as a static site generator. You write markdown + SQL, it builds a fast, beautiful dashboard.
    - **Why it matters:** Your entire reporting pipeline becomes code. Git-versioned, reproducible, and incredibly fast. No more "waiting for the model to refresh."

### 2. NHS-R & NHS.pycom Community (2025 Updates)
The open-source movement in the NHS is maturing rapidly. Key relevant talks from RPySOC 2025:
- **"Word is better than Quarto?"** (Jacqueline Grout & Matt Dray): A provocative look at report generation.
- **"Modelling Community waiting lists with NHS-R waiting list library"** (Simon Wellesley-Miller): Pre-built libraries for common NHS problems.
- **"Deploying Python in production"** (Amadeus Stevenson): Moving from local scripts to reliable pipelines.
- **NHS.pycom:** A dedicated Python community within the NHS, mirroring the success of NHS-R.

### 3. Geospatial: DuckDB + GeoPandas
Instead of struggling with Power BI's map visuals or waiting for ArcGIS licenses:
- **DuckDB 1.x** has powerful geospatial extensions that can join millions of points (e.g., patient postcodes) to polygons (ICB boundaries) in seconds.
- Combine with **GeoPandas** in Python for exploratory analysis, then render in Evidence.dev or Quarto.

### 4. Quarto for Automated Reporting
If you need to generate 50 PDF reports for different trusts/regions:
- **Quarto** (successor to RMarkdown) is the industry standard.
- Supports Python/Jupyter natively.
- Can output high-quality Word documents (crucial for NHS management who "need it in Word"), PDFs, and HTML.
- **Action:** Use Quarto to automate the "monthly board report" grind.

---
**Recommendation:** Start by experimenting with **DuckDB** on a local CSV/Excel dump that is currently slow in Excel/Power BI. The speed difference will be immediate.
