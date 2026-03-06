# Discovery Cycle — 2026-03-06 12:00 UTC

**Focus Areas:** NHS Python tools, data analytics, report automation

---

## 🔥 Top Finds

### 1. NHSDigital/data-analytics-services — Official NHS England Analytics Codebase

**Source:** https://github.com/NHSDigital/data-analytics-services

This is the official NHS Digital/Data Services analytics repository. Contains 30+ open-source projects from NHS England's Data Science team.

**Key Repos for John:**

| Repo | Description | Language |
|------|-------------|----------|
| **codonPython** | Reduce barrier to entry for NHS analysis; coding standards & reusable blocks | Python |
| **medicines-text-mining-tool** | NLP for extracting medicine info from text | Python, PySpark |
| **nhs_time_of_travel** | Interactive mapping tool for health/social care decision-making | Python |
| **artificial-data-generator** | Generate anonymous artificial NHS data in Databricks | Python, PySpark |
| **DNAttend** | ML framework predicting patient non-attendance (DNA) | Python |
| **Forecasting** | Different forecasting methods for NHS situations | Python |
| **SystemHierarchies** | Visualise NHS organisation structure & mapping | Python |

**Why Interesting:** These are production-grade tools from NHS England. The codonPython package is particularly relevant — it's designed specifically to help new analysts get started with NHS data work.

**Contact:** england.RAPchampions@nhs.net (they respond promptly)

---

### 2. codonPython — NHS Digital's Official Python Library

**Source:** https://github.com/NHSDigital/codonPython

> "In biological terms, a codon is one of the building blocks that make up our DNA. By openly sharing our code we hope that others will be able to take those blocks of code to build their own processes."

**Purpose:**
- Increase code sharing across NHS analysts
- Standardise coding standards
- Reduce barrier to entry for analysis
- Provide software development experience for analysts

**Install:**
```bash
python -m pip install --user git+https://github.com/codonlibrary/codonPython.git
```

**Why Interesting:** This is the closest thing to an "official" NHS Python package. It provides reusable code blocks specifically designed for NHS data work.

---

### 3. nhs-numbers — Python Package for NHS Number Validation

**Source:** https://github.com/search?q=nhs-numbers

A Python package providing utilities for NHS Numbers:
- Validity checks (checksum verification)
- Normalisation (formatting)
- Generation

**Why Interesting:** Essential for any NHS data cleaning pipeline. NHS Numbers follow a specific checksum algorithm — this package validates them automatically.

---

### 4. Data Validation for Polars — 2025 Survey

**Source:** [Pointblank Blog](https://posit-dev.github.io/pointblank/blog/validation-libs-2025/)

Key finding confirmed: **Great Expectations still lacks native Polars support** (as of 2025).

**Polars-Native Alternatives:**

| Library | Stars | Best For |
|---------|-------|----------|
| **Pandera** | 3,838 | Statistical testing, schema validation |
| **Patito** | 468 | Pydantic integration |
| **Pointblank** | 173 | Interactive reports, stakeholder communication |
| **Validoopsie** | 63 | Lightweight, logging, composable |

**NHS Relevance:** For NHS data quality pipelines, Pointblank's interactive HTML reports are excellent for sharing validation results with non-technical stakeholders (clinical leads, managers).

---

### 5. Python Email Report Automation Template

**Source:** https://github.com/CNuge/email-report

A modular template for scraping data and sending scheduled email reports.

**Key Features:**
- Cron-based scheduling
- Modular design for different data sources
- HTML email output with visualizations
- Simple to customize for NHS reporting needs

**Use Case:** Perfect for weekly/monthly NHS operational reports — automatically pull data, generate charts, email to distribution list.

---

## 📦 Quick Wins for John

### This Week

1. **Install codonPython** — `pip install git+https://github.com/codonlibrary/codonPython.git`
2. **Try nhs-numbers** for validating NHS numbers in any datasets
3. **Clone NHSDigital repos** — especially nhs_time_of_travel for mapping ideas

### This Month

4. **Set up email-report template** for automated weekly reports
5. **Evaluate Pandera or Pointblank** for Polars data validation (if moving from Pandas)

---

## 🔗 Links

- [NHSDigital/data-analytics-services](https://github.com/NHSDigital/data-analytics-services)
- [codonPython](https://github.com/NHSDigital/codonPython)
- [codonPython Docs](https://codonlibrary.github.io/codonPython/)
- [email-report template](https://github.com/CNuge/email-report)
- [Pointblank Validation Blog](https://posit-dev.github.io/pointblank/blog/validation-libs-2025/)

---

*Generated: 2026-03-06 12:00 UTC | Curious Collector*