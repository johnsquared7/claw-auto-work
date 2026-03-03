# Discovery: Automated EDA & SQL Optimization Tools for NHS Workflows

**Date:** 2026-03-03  
**Category:** Data Analysis / SQL Optimization / Automated Reporting  
**Quality:** Unique tools not covered in previous discoveries

---

## TL;DR

Three categories of NEW tools that complement previous discoveries (Polars, DuckDB, Quarto, Superset):

1. **ydata-profiling & SweetViz** — Instant exploratory data analysis reports
2. **PawSQL** — Open-source SQL rewrite + index optimizer (PostgreSQL/MySQL)
3. **Releem** — AI-powered MySQL performance monitoring

---

## 1. ydata-profiling — Instant EDA Reports

**What:** Generates comprehensive HTML data profiling reports from any DataFrame  
**Why it matters:** Replaces hours of manual EDA with one command. Perfect for quickly understanding new NHS datasets.

### What It Produces
- Overview: rows, columns, missing values, duplicates
- Variable types and distributions
- Correlation matrices
- Missing value patterns
- Sample data preview

### NHS Use Case
```python
from ydata_profiling import ProfileReport
import pandas as pd

# Load patient activity data
df = pd.read_csv("monthly_activity.csv")

# Generate profiling report
profile = ProfileReport(
    df, 
    title="A&E Activity Report - February 2026",
    minimal=True  # Faster for large datasets
)

# Save to HTML
profile.to_file("ae_activity_profile.html")

# Or display in notebook
profile.to_notebook()
```

### SweetViz — Dataset Comparison
For comparing two datasets (e.g., this month vs last month):
```python
import sweetviz as sv

# Compare current vs previous month
current = pd.read_csv("march_data.csv")
previous = pd.read_csv("february_data.csv")

report = sv.compare([previous, "February"], [current, "March"], "patient_id")
report.show_html("month_comparison.html")
```

### Comparison: ydata-profiling vs SweetViz

| Feature | ydata-profiling | SweetViz |
|---------|-----------------|----------|
| Single dataset profiling | ✅ Excellent | ✅ Good |
| Dataset comparison | ✅ Good | ✅ Excellent |
| Missing value analysis | ✅ Excellent | ✅ Good |
| Memory efficient | ✅ (minimal mode) | ✅ |
| Notebook integration | ✅ | ✅ |

### Resources
- **ydata-profiling:** https://github.com/ydataai/ydata-profiling
- **SweetViz:** https://github.com/fbdesignpro/sweetviz
- **Install:** `pip install ydata-profiling sweetviz`

---

## 2. PawSQL — SQL Rewrite + Index Optimization

**What:** Open-source SQL optimization tool with intelligent rewrite suggestions and index recommendations  
**Why it matters:** Unlike basic query explainers, PawSQL actively rewrites queries for better performance.

### Key Features
- **SQL Rewrite:** Converts inefficient patterns to optimized versions
- **Index Advisor:** Recommends which columns to index
- **Audit Rules:** Checks for anti-patterns (SELECT *, N+1 queries, etc.)
- **Supports:** PostgreSQL, MySQL, Oracle, MariaDB, openGauss

### Example: Query Optimization

**Before (slow):**
```sql
SELECT * FROM patient_activity 
WHERE department = 'A&E' 
AND admission_date >= '2026-01-01'
AND status = 'discharged';
```

**After (PawSQL optimization):**
```sql
SELECT patient_id, department, admission_date, discharge_time, status 
FROM patient_activity 
WHERE department = 'A&E' 
AND admission_date >= '2026-01-01'::date
AND status = 'discharged'
-- Suggests: CREATE INDEX idx_dept_date_status 
-- ON patient_activity(department, admission_date, status);
```

### Installation Options

**Option 1: CLI (PostgreSQL)**
```bash
# Install PawSQL CLI
wget https://download.pawsql.com/pawsql-ce-2.3.0-linux-x86_64.tar.gz
tar -xzf pawsql-ce-2.3.0-linux-x86_64.tar.gz
cd pawsql-ce/bin

# Analyze a query
./pawsql-cli -U postgres -d nhs_data -q "SELECT * FROM patient_activity WHERE..."
```

**Option 2: IntelliJ Plugin**
- Install from JetBrains Marketplace
- Works with DataGrip, PyCharm, VS Code (via JetBrains Gateway)

**Option 3: Docker**
```bash
docker run -d -p 8080:8080 pawsql/pawsql-ce
# Web UI at http://localhost:8080
```

### NHS Use Case
```python
# Python integration via subprocess
import subprocess

def optimize_query(query, db_config):
    result = subprocess.run([
        "./pawsql-cli",
        "-U", db_config["user"],
        "-P", db_config["password"],
        "-d", db_config["database"],
        "-q", query,
        "--format", "json"
    ], capture_output=True, text=True)
    
    import json
    return json.loads(result.stdout)

# Example
query = """
SELECT d.name, COUNT(p.id) as patient_count
FROM departments d
LEFT JOIN patient_activity p ON d.id = p.department_id
WHERE p.admission_date >= '2026-01-01'
GROUP BY d.name
"""
result = optimize_query(query, db_config)
print(result["optimized_query"])
print(result["index_recommendations"])
```

### Resources
- **GitHub:** https://github.com/PawSQL/pawsql-ce
- **Docs:** https://docs.pawsql.com/
- **Download:** https://download.pawsql.com/

---

## 3. Releem — AI-Powered MySQL Performance

**What:** Continuous MySQL performance monitoring with automated tuning  
**Why it matters:** For NHS systems using MySQL/PostgreSQL, Releem proactively identifies slow queries and suggests configuration changes.

### How It Works
1. **Install agent** on database server
2. **Monitors queries** in real-time
3. **Identifies slow queries** and suggests optimizations
4. **Tunes MySQL configuration** automatically

### Releem vs Other Tools

| Feature | Releem | SQLAI.ai | PawSQL |
|---------|--------|----------|--------|
| Query optimization | ✅ | ✅ | ✅ |
| Auto config tuning | ✅ | ❌ | ❌ |
| Continuous monitoring | ✅ | ❌ | ❌ |
| Free tier | ✅ (limited) | ✅ | ✅ |
| MySQL focus | ✅ | ❌ | ❌ |

### When to Use
- **MySQL/MariaDB** databases (PostgreSQL support limited)
- Production systems needing ongoing monitoring
- When you want automated configuration tuning, not just query analysis

### Resources
- **Website:** https://Releem.com
- **GitHub:** https://github.com/releem

---

## Integration: Updated Recommended Stack

```
┌─────────────────────────────────────────────────────────┐
│                    DATA SOURCES                          │
│   Supabase (PostgreSQL)    │    CSV/Excel files        │
└──────────────┬──────────────┴──────────────┬───────────┘
               │                              │
               ▼                              ▼
┌──────────────┴────────────────────────────┴───────────┐
│                   PROCESSING                              │
│   DuckDB (ad-hoc SQL)    │    Polars (ETL)             │
└──────────────┬────────────────────────────┬─────────────┘
               │                            │
               ▼                            ▼
┌──────────────┴────────────────────────────┴─────────────┐
│                  QUALITY & ANALYSIS                        │
│   Great Expectations (validation) │ ydata-profiling (EDA)│
└──────────────┬────────────────────────────┬──────────────┘
               │                            │
               ▼                            ▼
┌──────────────┴────────────────────────────┴─────────────┐
│                   OPTIMIZATION                             │
│   PawSQL (query rewrite/index) │ Releem (MySQL tuning)   │
└──────────────┬────────────────────────────────────────────┘
               │
               ▼
┌──────────────┴────────────────────────────────────────────┐
│                   OUTPUT                                    │
│   Quarto (parameterized HTML/PDF reports)                  │
│   Apache Superset (self-service dashboards)                │
│   Streamlit (interactive internal tools)                  │
└────────────────────────────────────────────────────────────┘
```

---

## Quick Wins to Try This Week

1. **Generate EDA report** — `pip install ydata-profiling` — run on any NHS dataset
2. **Compare months** — Use SweetViz to compare February vs March activity data
3. **Test PawSQL** — Run Docker version: `docker run -d -p 8080:8080 pawsql/pawsql-ce`

---

## Sources

- ydata-profiling: https://github.com/ydataai/ydata-profiling
- SweetViz: https://github.com/fbdesignpro/sweetviz
- PawSQL: https://github.com/PawSQL/pawsql-ce
- Releem: https://github.com/releem
- KDnuggets: https://www.kdnuggets.com/10-lesser-known-python-libraries-every-data-scientist-should-be-using-in-2026
- Medium: https://medium.com/@harishk3493/effortless-eda-with-sweetviz-ydata-profiling-secret-weapons-for-every-data-scientist-1c03625e4e8c
