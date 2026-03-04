# Discovery: NHS Digital Analytics, PDF Reporting & SQL Window Functions

**Date:** 2026-03-04  
**Category:** NHS Analytics / Python / SQL / Report Automation  
**Quality:** High — NHS-specific resources and practical tools for John's workflow

---

## TL;DR

6 discoveries for John's NHS analyst workflow:
1. **NHSDigital/data-analytics-services** — Official NHS Digital open-source analytics repos
2. **codonPython** — NHS Digital's Python library for reducing analyst barriers
3. **MedicalMap** — NHS Python Community + Google Health Streamlit mapping tool
4. **WeasyPrint + Jinja2** — Professional PDF reports from Pandas DataFrames
5. **FPDF2** — Modern DataFrame-to-PDF library
6. **PostgreSQL Window Functions** — Time-series analysis for patient data

---

## 1. NHSDigital/data-analytics-services — Official NHS Python Resources

**Repo:** https://github.com/NHSDigital/data-analytics-services  
**What:** Central hub for NHS Digital's open-source analytics work

This is the official NHS Digital Analytics Services GitHub organization — a goldmine for NHS analysts. They share production-grade code used within NHS England.

### Key Repos for John's Workflow:

| Repo | Description | Language |
|------|-------------|----------|
| [codonPython](https://github.com/NHSDigital/codonPython) | Reduce barriers for new analysts at NHS Digital | Python |
| [artificial-data-generator](https://github.com/NHSDigital/artificial-data-generator) | Generate anonymous synthetic data in Databricks | Python, PySpark |
| [medicines-text-mining-tool](https://github.com/NHSDigital/medicines-text-mining-tool) | Text mining for medicines data | Python, PySpark |
| [data-viz-community-of-practice](https://github.com/NHSDigital/data-viz-community-of-practice) | Data viz best practices across NHS | Various |

### Why It Matters:
- Production-ready code used in actual NHS data pipelines
- Follows NHS RAP (Reproducible Analytical Pipelines) standards
- Contact: **england.RAPchampions@nhs.net** for support

---

## 2. codonPython — NHS Digital's Analyst-Friendly Library

**Repo:** https://github.com/NHSDigital/codonPython  
**Purpose:** "Aim to reduce the DAE (Data Access Environment) barrier for new analysts at NHSD"

**What:** A Python library specifically designed to help new analysts work with NHS data systems more easily.

### Potential Use Cases:
- Simplified data extraction helpers
- Common NHS data transformations
- Standardised naming conventions for NHS datasets

### Contact:
- Raise issues on GitHub for support
- Or email: england.RAPchampions@nhs.net

---

## 3. MedicalMap — NHS Python Community + Google Health

**Repo:** https://github.com/nhs-pycom/nhs_time_of_travel  
**Demo:** https://nhs-time-of-travel.streamlit.app/

**What:** A collaborative open-source project between **NHS Python Community** and **Google Health**, building interactive mapping tools for health and social care decision-making.

### Features:
- Streamlit-based interactive maps
- Time-of-travel analysis for healthcare access
- Can be adapted for:
  - Patient flow analysis
  - Service coverage mapping
  - Resource allocation planning

### Why It Matters:
- Shows what's possible with Streamlit + NHS data
- Good reference for building similar interactive tools
- Built by NHS Python Community (nhs-pycom)

---

## 4. WeasyPrint + Jinja2 — Professional PDF Reports

**WeasyPrint:** https://doc.courtbouillon.org/weasyprint/  
**Guide:** https://pbpython.com/pdf-reports.html

**What:** Convert Pandas DataFrames + Jinja2 templates to professional PDF reports

### Why It Matters for NHS:
- Generate branded NHS reports automatically
- Include charts from Matplotlib
- Parameterized reports (different departments, months)

### Basic Example:
```python
from jinja2 import Template
from weasyprint import HTML
import pandas as pd

# Load data
df = pd.read_sql(query, connection)

# Template with NHS styling
template = Template("""
<h1>NHS Trust Report</h1>
<p>Period: {{ month }}</p>
<table>
{% for row in data %}
<tr><td>{{ row.name }}</td><td>{{ row.value }}</td></tr>
{% endfor %}
</table>
""")

# Generate PDF
html_out = template.render(month="2026-01", data=df.to_dict('records'))
HTML(string=html_out).write_pdf("report.pdf")
```

### Resources:
- **Practical Business Python Guide:** https://pbpython.com/pdf-reports.html
- **Install:** `pip install weasyprint jinja2`

---

## 5. FPDF2 — Modern DataFrame-to-PDF

**Repo:** https://github.com/PyFPDF/fpdf2  
**Docs:** https://pyfpdf.github.io/fpdf2/

**What:** Modern, maintained fork of FPDF for PDF generation in Python

### Why It Matters:
- Simpler than ReportLab for basic tables
- Works well with Pandas DataFrames
- Active development (unlike original FPDF)

### Example:
```python
from fpdf import FPDF
import pandas as pd

pdf = FPDF()
pdf.add_page()
pdf.set_font("Arial", size=12)

df = pd.read_sql(query, connection)
pdf.cell(200, 10, txt="NHS Department Report", ln=True, align='C')

for index, row in df.iterrows():
    pdf.cell(0, 10, txt=f"{row['department']}: {row['count']}", ln=True)

pdf.output("report.pdf")
```

### Alternative: dataframetopdf
**Repo:** https://github.com/JohnFunkCode/dataframetopdf  
Specialized for converting DataFrames directly to PDF using ReportLab platypus.

---

## 6. PostgreSQL Window Functions — Time-Series Healthcare Data

### Key Functions for NHS Data:

#### time_bucket() — Grouping Time Series
```sql
-- Daily admissions using time_bucket (TimescaleDB extension)
SELECT time_bucket('1 day', admission_date) AS day,
       COUNT(*) AS admissions
FROM patient_admissions
GROUP BY time_bucket('1 day', admission_date)
ORDER BY day;
```

#### Running Totals with window frames
```sql
-- Running total of bed days per ward
SELECT 
    ward_id,
    admission_date,
    bed_days,
    SUM(bed_days) OVER (
        PARTITION BY ward_id 
        ORDER BY admission_date 
        ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW
    ) AS running_total_bed_days
FROM ward_stays;
```

#### LAG/LEAD — Compare Periods
```sql
-- This month vs last month admissions
SELECT 
    admission_month,
    admissions,
    LAG(admissions, 1) OVER (ORDER BY admission_month) AS prev_month,
    admissions - LAG(admissions, 1) OVER (ORDER BY admission_month) AS change
FROM monthly_admissions;
```

#### ROW_NUMBER — Identify Duplicate Spells
```sql
-- Find duplicate spell IDs (common NHS data quality issue)
SELECT *,
    ROW_NUMBER() OVER (PARTITION BY spell_id ORDER BY episode_start_date) AS rn
FROM hes_episodes
WHERE rn > 1;
```

### Resources:
- **Crunchy Data Window Functions Guide:** https://www.crunchydata.com/blog/window-functions-for-data-analysis-with-postgres
- **LearnSQL COVID Analysis:** https://learnsql.com/blog/analyze-time-series-covid19-data-sql-window-functions/

---

## Quick Reference: Install Commands

```bash
# PDF Generation
pip install weasyprint jinja2
pip install fpdf2

# NHS Data (if applicable)
pip install codonpython  # Check if available on PyPI

# SQL Analysis
# No install needed - these are native SQL features
```

---

## Next Steps for John

1. **Explore NHS Digital repos** — Start with codonPython if it matches your data environment
2. **Try WeasyPrint** — Good for automated monthly reports with NHS branding
3. **Practice window functions** — Particularly useful for:
   - Calculating running totals (bed days)
   - Comparing time periods (month-over-month)
   - Identifying duplicate records

---

*Generated: 2026-03-04 02:00 UTC*
*Focus: NHS analyst workflow — Python, SQL, Report Automation*
