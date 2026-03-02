# Discovery: Report Automation & BI Alternatives for NHS Workflows

**Date:** 2026-03-02  
**Category:** Report Automation / Business Intelligence  
**Quality:** Targeted for NHS/Healthcare analyst workflows

---

## TL;DR

New tools complementing the March 1st discoveries (Polars, DuckDB, EverSQL):

1. **Quarto** — Automated parameterized reports (already used by NHS-R Community!)
2. **ReportLab** — Python-native PDF generation with tables and charts
3. **Apache Superset** — Open-source BI alternative to Power BI
4. **SQLAI.ai** — Free online SQL optimizer (no signup required)
5. **Great Expectations** — Data quality testing and validation

---

## 1. Quarto — Parameterized Reports at Scale

**What:** Next-gen RMarkdown; publishes Python/R notebooks to PDF, HTML, Word  
**Why it matters:** Generate hundreds of department-specific reports from ONE template.

### NHS-R Community is Already Using It
The **NHS England R Community** (nhs-r-reporting) uses Quarto for RAP-compliant analytical reports:
- NHS theme available on GitHub
- Works with Plotly for interactive charts
- Parameters generate multiple report versions for different organisations
- Uses `{targets}` for automated data pipeline dependencies

### Example: Monthly Department Report
```yaml
# _quarto.yml
project:
  type: website
  output-dir: _site

params:
  department: "A&E"
  month: "2026-01"
```

```python
# report.qmd
---
params:
  department: "A&E"
  month: "2026-01"
---

# {{ params.department }} Activity Report - {{ params.month }}

```{python}
import pandas as pd
df = pd.read_csv(f"activity_{params.month}.csv")
dept_df = df[df.department == params.department]
```

Total Patients: `{python} len(dept_df)`
```

### Generating All Department Reports
```python
from quartodoc import render
import subprocess

departments = ["A&E", "Cardiology", "Orthopaedics", "ICU"]
for dept in departments:
    subprocess.run([
        "quarto", "render", "report.qmd",
        "--param", f"department={dept}"
    ])
```

### Resources
- **NHS-R Community:** https://nhsengland.github.io/nhs-r-reporting/
- **Quarto Parameterized Reports:** https://quarto.org/docs/blog/posts/2025-07-24-parameterized-reports-python/
- **Install:** `pip install quarto` (or `conda install quarto`)

---

## 2. ReportLab — PDF Generation with Python

**What:** Mature Python library for programmatic PDF creation  
**Why it matters:** Generate branded NHS reports directly — no manual formatting.

### Comparison with Alternatives

| Feature | ReportLab | WeasyPrint | FPDF |
|---------|-----------|------------|------|
| Table support | Excellent | Good | Basic |
| Charts | Yes (via drawing) | Limited | No |
| Learning curve | Medium | Low | Low |
| NHS use case | Branded reports | Simple HTML→PDF | Receipts |

### Basic Example
```python
from reportlab.lib.pagesizes import letter
from reportlab.pdfgen import canvas
from reportlab.lib import colors

def create_nhs_report(filename, data):
    c = canvas.Canvas(filename, pagesize=letter)
    
    # Header
    c.setFont("Helvetica-Bold", 16)
    c.drawString(100, 750, "NHS Trust - Activity Report")
    c.setFont("Helvetica", 10)
    c.drawString(100, 735, f"Generated: {pd.Timestamp.now().strftime('%Y-%m-%d')}")
    
    # Table
    data = [["Department", "Patients", "Avg Wait (mins)"]] + data
    table = Table(data, colWidths=[200, 100, 150])
    table.setStyle(TableStyle([
        ('BACKGROUND', (0, 0), (-1, 0), colors.navy),
        ('TEXTCOLOR', (0, 0), (-1, 0), colors.whitesmoke),
        ('FONTSIZE', (0, 0), (-1, -1), 10),
        ('GRID', (0, 0), (-1, -1), 1, colors.black),
    ]))
    table.wrapOn(c, 400, 200)
    table.drawOn(c, 100, 500)
    
    c.save()

# Usage
data = [["A&E", "4,523", "47"], ["Cardiology", "1,892", "32"]]
create_nhs_report("monthly_report.pdf", data)
```

### For Complex Layouts
Use `SimpleDocTemplate` with paragraph styles for rich formatting:
```python
from reportlab.platypus import SimpleDocTemplate, Paragraph, Spacer
from reportlab.lib.styles import getSampleStyleSheet

doc = SimpleDocTemplate("report.pdf")
styles = getSampleStyleSheet()
story = [
    Paragraph("Monthly Activity Report", styles['Title']),
    Spacer(1, 12),
    Paragraph(f"Total patients: {total}", styles['Normal']),
]
doc.build(story)
```

### Resources
- **Docs:** https://docs.reportlab.com/
- **Install:** `pip install reportlab`

---

## 3. Apache Superset — Open-Source BI

**What:** Apache-licensed BI platform (100% free)  
**Why it matters:** Self-host Power BI-style dashboards without Microsoft licensing.

### Why Consider for NHS
- **Cost:** Free (no per-user licensing)
- **Data sovereignty:** Host on-premises or NHS cloud
- **SQL-native:** Write queries directly or use visual builder
- **Embedding:** Can embed dashboards in other apps

### vs Power BI

| Feature | Superset | Power BI |
|---------|----------|----------|
| Cost | Free | Per-user ($10+/mo) |
| Deployment | Self-host | Cloud/Desktop |
| Excel export | Yes | Yes |
| R/Python transforms | Limited | Advanced |
| Supabase connector | Yes (via Postgres) | Yes |

### Supabase Connection in Superset
```yaml
# Connect Superset to Supabase
Database: PostgreSQL
SQLAlchemy URI: postgresql://postgres:[password]@db.[project].supabase.co:5432/postgres
```

### Healthcare Considerations
- Use row-level security (RLS) for sensitive data
- Can connect to CSV/Parquet files directly (via GCS/S3)
- Supports NHS-like colour schemes

### Resources
- **Website:** https://superset.apache.org/
- **GitHub:** https://github.com/apache/superset
- **Self-host guide:** https://superset.apache.org/docs/installation/

---

## 4. SQLAI.ai — Free SQL Optimizer

**What:** Free online SQL query optimization tool  
**Why it matters:** Instant optimization suggestions without signup or subscription.

### Features
- **Free tier:** Unlimited query optimizations
- **Supports:** MySQL, PostgreSQL, SQL Server, Oracle
- **Explains:** What changed and why
- **No install:** Web-based

### How It Works
1. Paste slow query
2. Select database type (PostgreSQL)
3. Get optimized version + explanation

### Example Output
```
Original: 2.3s execution
Optimized: 0.1s execution

Suggestions:
• Add index on (department, date)
• Rewrite subquery as JOIN
• Use covering index
```

### Resources
- **Website:** https://www.sqlai.ai/sql-optimizer
- **Browser-based:** No installation needed

---

## 5. Great Expectations — Data Quality Testing

**What:** Python library for validating and documenting data quality  
**Why it matters:** Automate data quality checks in NHS reporting pipelines.

### Use Case: Validate Monthly Data
```python
import great_expectations as gx

# Define expectations
expectations = [
    gx.expectations.ExpectColumnValuesToNotBeNull(column="patient_id"),
    gx.expectations.ExpectColumnValuesToBeBetween(
        column="wait_time_minutes", min_value=0, max_value=1440
    ),
    gx.expectations.ExpectColumnDistinctValuesToBeInSet(
        column="department", value_set=["A&E", "Cardiology", "Surgery"]
    ),
]

# Validate
df = pd.read_csv("monthly_data.csv")
results = gx.validate(df, expectations)

if not results.success:
    print("Data quality issues found!")
    for issue in results.failures:
        print(f"  - {issue}")
```

### Integration with DAGs (Airflow/Luigi)
```python
# In your pipeline
def validate_data():
    df = extract_data()
    results = gx.validate(df, expectations)
    if not results.success:
        raise ValueError(f"Data quality failed: {results.failures}")
    return df
```

### Resources
- **Docs:** https://docs.greatexpectations.io/
- **Install:** `pip install great-expectations`
- **Quick start:** `gx check new`

---

## Integration: Recommended Stack for John's NHS Workflow

```
┌─────────────────────────────────────────────────────────┐
│                    DATA SOURCES                          │
│   Supabase (PostgreSQL)    │    CSV/Excel files        │
└──────────────┬──────────────┴──────────────┬─────────────┘
               │                            │
               ▼                            ▼
┌──────────────┴────────────────────────────┴─────────────┐
│                   PROCESSING                            │
│   DuckDB (ad-hoc SQL)    │    Polars (ETL/transform)   │
└──────────────┬────────────────────────────┬─────────────┘
               │                            │
               ▼                            ▼
┌──────────────┴────────────────────────────┴─────────────┐
│                  QUALITY CHECKS                          │
│        Great Expectations (automated validation)         │
└──────────────┬──────────────────────────────────────────┘
               │
               ▼
┌──────────────┴──────────────────────────────────────────┐
│                   OUTPUT                                 │
│   Quarto (parameterized HTML/PDF reports)               │
│   Apache Superset (self-service dashboards)              │
└──────────────────────────────────────────────────────────┘
```

---

## Quick Wins to Try This Week

1. **Install ReportLab** — `pip install reportlab` — try generating a simple table
2. **Test SQLAI.ai** — Paste a slow Supabase query at https://www.sqlai.ai/sql-optimizer
3. **Explore Quarto** — Run `quarto check` on existing Jupyter notebooks

---

## Sources

- Quarto docs: https://quarto.org
- NHS-R Community: https://nhsengland.github.io/nhs-r-reporting/
- ReportLab docs: https://docs.reportlab.com/
- Apache Superset: https://superset.apache.org/
- SQLAI.ai: https://www.sqlai.ai/sql-optimizer
- Great Expectations: https://docs.greatexpectations.io/
- Preset.io healthcare blog: https://preset.io/blog/open-source-analytics-for-healthcare/
