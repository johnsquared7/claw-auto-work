# Discovery: Python Data Tools for NHS Analytics
**Date:** 2026-03-04
**Source:** Autonomous Discovery Cycle

---

## Key Findings

### 1. Polars - High-Performance DataFrame Library
- **URL:** https://github.com/pola-rs/polars
- **Stars:** ~37k
- **Why interesting:** Written in Rust, significantly faster than pandas for large NHS datasets. Drop-in replacement for many pandas operations.
- **Relevance:** Perfect for large patient datasets, waiting list analytics, population health data

### 2. MarkItDown - Document Conversion
- **URL:** https://github.com/microsoft/markitdown
- **Stars:** ~86k+
- **Why interesting:** Converts PDF, Word, Excel, PowerPoint to Markdown. Preserves structure (headings, tables, lists)
- **Relevance:** Automate extraction from NHS reports, clinical documents, Excel spreadsheets

### 3. EverSQL - AI SQL Optimizer
- **URL:** https://www.eversql.com/
- **Why interesting:** AI-powered PostgreSQL & MySQL optimizer. 100k+ engineers use it.
- **Relevance:** Optimize slow NHS database queries, improve report generation speed

### 4. SQLAI.ai - Free AI SQL Optimizer
- **URL:** https://www.sqlai.ai/sql-optimizer
- **Why interesting:** Free tier available, AI model analyzes and optimizes queries
- **Relevance:** Quick query improvements without cost barrier

### 5. NHS Python Community (nhs-pycom)
- **URL:** https://nhs-pycom.net/
- **Why interesting:** Official NHS community championing Python in healthcare
- **Relevance:** Directly relevant to John's NHS analyst workflow, code examples, best practices

### 6. NHS-R plotthedots Python Implementation
- **URL:** https://github.com/nhs-pycom/nhspy-plotthedots
- **Why interesting:** SPC (Statistical Process Control) charts for NHS "Making Data Count" programme
- **Relevance:** Create compliant NHS quality dashboards with automatic signal detection

### 7. Sweetviz - Fast EDA
- **URL:** https://github.com/fbdesignpro/sweetviz
- **Why interesting:** One-line EDA reports, compares datasets, HTML output
- **Relevance:** Quick data quality checks on NHS datasets

### 8. Airflow - Workflow Automation
- **URL:** https://github.com/apache/airflow
- **Stars:** ~45k
- **Why interesting:** Schedule and monitor data pipelines programmatically
- **Relevance:** Automate weekly/monthly NHS reporting workflows

---

## Potential Workflow Improvements

1. **Data Processing:** Replace pandas with Polars for 10-100x speed on large datasets
2. **Report Automation:** Use MarkItDown + Python to extract and standardize NHS PDF reports
3. **Query Optimization:** Run slow queries through EverSQL/SQLAI before production
4. **SPC Charts:** Implement NHS-compliant process behaviour charts using plotthedots
5. **Pipeline Scheduling:** Set up Airflow for automated weekly reporting

---

## Tags
#python #nhs #data-analysis #sql #automation #healthcare
