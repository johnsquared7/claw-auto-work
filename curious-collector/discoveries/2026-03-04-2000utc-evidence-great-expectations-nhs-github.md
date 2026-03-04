# Discovery: Evidence.dev, Great Expectations & NHS GitHub Resources
**Date:** 2026-03-04 20:00 UTC | **Source:** Autonomous Discovery Cycle

---

## 🔑 Key Finding: Evidence.dev — BI as Code

**URL:** https://evidence.dev/

**URL:** https://github.com/evidence-dev/evidence

Evidence is an **open-source framework for building data products with SQL**. Instead of drag-and-drop BI, you write markdown files with embedded SQL queries that render into interactive dashboards.

**Why it's interesting for NHS analysts:**

| Feature | Benefit for NHS |
|---------|-----------------|
| SQL + Markdown | Version-controlled reports in Git |
| Static site generation | Easy hosting on GitHub Pages |
| No drag-drop | Reproducible, reviewable code |
| Auto-documented | Each query = docs + viz |
| PostgreSQL, MySQL, SQLite, DuckDB support | Works with NHS data sources |

**How it works:**
```markdown
<!-- monthly-waiting-list.md -->
# Waiting List Report

```sql patients_by_specialty
SELECT 
    specialty,
    COUNT(*) as total_patients,
    AVG(wait_weeks) as avg_wait
FROM waiting_list
GROUP BY specialty
```

{#if data.patients_by_specialty}
| Specialty | Patients | Avg Wait (weeks) |
|-----------|----------|------------------|
{#each data.patients_by_specialty}
| {specialty} | {total_patients} | {avg_wait} |
{/each}
{/if}
```

**NHS use case:** Monthly waiting list reports, bed occupancy dashboards, A&E metrics — all version-controlled and auto-generated from SQL.

**Comparison to Power BI:**
| Aspect | Power BI | Evidence.dev |
|--------|----------|--------------|
| Learning curve | Medium (UI) | Low (SQL + Markdown) |
| Version control | Poor | Excellent (Git) |
| Collaboration | Shared .pbix files | PRs + code review |
| Cost | License required | Free (open source) |

**Stars:** 9.5k+ on GitHub | Rising rapidly in 2026

---

## 🧪 Great Expectations (GX Core) — Data Quality Testing

**URL:** https://greatexpectations.io/

**URL:** https://github.com/great-expectations/great_expectations

Great Expectations is a Python-based **data quality framework** that lets you write "expectations" — tests that describe what valid data should look like.

**Why it's relevant for NHS data:**

```python
import great_expectations as gx

# Define expectations for NHS waiting list data
expectations = [
    gx.expectations.ExpectColumnValuesToNotBeNull(column="patient_id"),
    gx.expectations.ExpectColumnValuesToBeBetween(column="wait_weeks", min_value=0, max_value=156),
    gx.expectations.ExpectColumnValueLengthsToBeBetween(column="specialty", min_value=3, max_value=100),
    gx.expectations.ExpectColumnDistinctValuesToBeInSet(
        column="status", 
        value_set=["waiting", "treated", "removed"]
    ),
]

# Validate and get results
results = validator.validate(expectations=expectations)
```

**Key features:**
- **Data Docs** — Auto-generated HTML reports showing what passed/failed
- **Integrations** — Works with Pandas, Spark, SQL databases, Airflow
- **CI/CD ready** — Block bad data from entering pipelines
- **Collaborative** — Expectations = shared language between analysts and stakeholders

**NHS use case:**
- Validate SUS data extracts on import
- Check waiting list data meets business rules
- Automated data quality checks before reporting
- Alert when new data falls outside expected ranges

** GX Core (newer, lighter):**
TheGX Core library is the streamlined 2026 version — less overhead, focused on validation.

---

## 🏥 NHS GitHub Resources — Directly Relevant

### 1. NHS Python Community
**URL:** https://github.com/nhs-oa-community/nhs.pycom

> "The NHS Python Community website"

This is the official community championing Python in the NHS. They run:
- Python learning sessions for NHS staff
- Code clubs and workshops
- Shared libraries and tools

**Related repos:**
- `nhs-oa-community/coding-club` — Python learning sessions developed by NHSX Analytics Unit
- `nhs-oa-community/nhs_time_of_travel` — Google Health collaboration for NHS travel analysis

### 2. NHS Digital Data Analytics Services
**URL:** https://github.com/NHSDigital/data-analytics-services

> "This repo collects the open-source work of the Analytics Service within NHS Digital Data Services"

Real analytics code from NHS Digital — including:
- Reproducible Analytical Pipelines (RAP)
- Data processing workflows
- Statistical analysis

### 3. NHS England RAP Package Template
**URL:** https://github.com/NHSDigital/rap-package-template

> "A python package template by NHS England that can be adapted for RAP projects"

**Reproducible Analytical Pipelines (RAP)** are the NHS standard for transparent, reproducible analysis. This template gives you:
- Standard Python package structure
- Testing setup
- Documentation templates
- CI/CD configuration

**Why it matters:** If John wants to move from manual Power BI reports to automated, version-controlled Python pipelines, this is the starting point.

### 4. NHS-R Community — Statistical Process Control
**URL:** https://github.com/nhs-r-community/NHSRplotthedots

> "An SPC package to support NHS England's 'Making Data Count' programme"

Python may be preferred, but R has excellent NHS-specific tools:
- SPC (Statistical Process Control) charts
- Automatic signal detection for process changes
- NHS England compliant visualizations

**Related:** `johnmackintosh/spccharter` — Creates SPC charts automatically detecting signals of process change

### 5. NHS Digital Artificial Data Generator
**URL:** https://github.com/NHSDigital/artificial-data-generator

> "Pipelines for generating large volumes of anonymous artificial data that share some of the data"

**Use characteristics of real NHS case:** Create synthetic test data for development without using real patient data (GDPR/compliance friendly).

---

## 🔧 Tool Comparison for Today's NHS Analyst

| Need | Solution | Notes |
|------|----------|-------|
| Code-based dashboards | Evidence.dev | SQL + Markdown → website |
| Data quality testing | Great Expectations | Python expectations |
| Reproducible pipelines | NHS RAP Template | Start point for automation |
| Learning Python | NHS Python Community | Free training & resources |
| Synthetic test data | NHS Artificial Data Generator | GDPR-safe development |
| SPC charts | NHSRplotthedots / spccharter | NHS England compliant |

---

## 🎯 Relevance to John's NHS Workflow

| Pain Point | Solution from This Discovery |
|------------|------------------------------|
| Power BI licensing costs | Evidence.dev (free, SQL-based) |
| Manual data quality checks | Great Expectations (automated) |
| Moving to Python pipelines | NHS RAP Package Template |
| Need NHS-specific examples | NHS Digital GitHub repos |
| Version-controlled reports | Evidence.dev + Git |

---

## 🔭 Next Steps

1. **Try Evidence.dev** — Spin up a quick demo with sample NHS data
2. **Install Great Expectations** — Run validation on a current dataset
3. **Explore NHS RAP Template** — Assess for future pipeline work

---

*Discovery completed 2026-03-04 20:00 UTC*
