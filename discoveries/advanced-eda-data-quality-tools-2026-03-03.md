# Discovery: Advanced EDA & Data Quality Tools for NHS Analysts

**Date:** 2026-03-03  
**Category:** Exploratory Data Analysis / Data Quality  
**Quality:** Unique tools not covered in March 1-2 discoveries

---

## TL;DR

Five tools that complement the existing stack (Polars, DuckDB, Quarto):
1. **ydata-profiling** — Instant EDA reports (successor to pandas-profiling)
2. **Vaex** — Process billions of rows on a laptop (out-of-core DataFrames)
3. **D-Tale** — Interactive GUI for exploring pandas DataFrames
4. **Pandera** — Schema validation with type hints for pandas
5. **Pyjanitor** — Clean method-chaining API for data cleaning

---

## 1. ydata-profiling — Instant EDA Reports

**What:** Generates comprehensive HTML data profiles from pandas DataFrames  
**Why it matters:** What takes hours of manual EDA, ydata-profiling does in seconds.

### NHS Use Case
```python
import pandas as pd
from ydata_profiling import ProfileReport

df = pd.read_csv("monthly_appointments.csv")
profile = ProfileReport(df, title="A&E Activity Report")
profile.to_file("ae_profile.html")
```

### What You Get
- Summary statistics for every column
- Correlation matrix (Pearson, Spearman, Kendall)
- Missing value analysis
- Distribution charts
- Flagged warnings (e.g., high cardinality, zeros, skewness)

### Why "ydata" Instead of "pandas-profiling"?
The library was renamed in 2023. Both work, but `ydata-profiling` is the current version.

### Comparison: Manual vs ydata-profiling

| Task | Manual | ydata-profiling |
|------|--------|-----------------|
| Missing values | `df.isnull().sum()` | Auto-detected with % |
| Correlations | Manual heatmap | Built-in, multiple methods |
| Distributions | `df[col].hist()` | Auto-generated for all cols |
| Time | ~2 hours | ~30 seconds |

### Install
```bash
pip install ydata-profiling
```

---

## 2. Vaex — Billions of Rows on a Laptop

**What:** Lazy out-of-core DataFrame library (processes data without loading into RAM)  
**Why it matters:** When Polars isn't enough and you have datasets too large for memory.

### When to Use Vaex vs Polars

| Scenario | Tool |
|----------|------|
| 1-10 million rows | Polars |
| 10-100 million rows | Polars or Vaex |
| 100+ million rows | Vaex |
| Doesn't fit in RAM | Vaex |
| Want fastest possible | Polars |

### NHS Use Case: Huge Historical Data
```python
import vaex

# Opens 50GB file without loading into memory
df = vaex.open("/path/to/large/appointments.hdf5")

# Lazy operations - no memory used until collect
result = df.groupby('department', agg={'patient_id': 'count'})
print(result)  # Only now computes
```

### Key Features
- Memory-mapped files (HDF5, Parquet, Arrow)
- Virtual columns (computed on the fly)
- Strided arrays for efficiency
- Integrates with Jupyter for visualization

### Install
```bash
pip install vaex
```

---

## 3. D-Tale — Interactive Data GUI

**What:** Spreadsheet-like interface for pandas DataFrames in Jupyter  
**Why it matters:** Explore data visually without writing exploration code.

### NHS Use Case
```python
import pandas as pd
import dtale

df = pd.read_csv("waiting_list.csv")
dtale.show(df)
```

This launches a web interface where you can:
- Sort columns by clicking headers
- Filter with point-and-click
- Build charts (bar, line, scatter, heatmap)
- View column correlations
- Export filtered data

### Use When
- Quick data inspection during development
- Sharing data with non-technical stakeholders
- Finding patterns before writing production code
- Debugging data transformations

### Comparison: D-Tale vs ydata-profiling

| Feature | D-Tale | ydata-profiling |
|---------|--------|-----------------|
| Interactivity | Yes (filter, sort) | No (static report) |
| Speed | Moderate | Fast |
| Best for | Exploration | Documentation |
| Export | CSV, Excel | HTML, JSON |

### Install
```bash
pip install dtale
```

---

## 4. Pandera — Schema Validation for DataFrames

**What:** Type-hinting and schema validation for pandas DataFrames  
**Why it matters:** Catch data quality issues at runtime, not in downstream reports.

### The Problem
Your pipeline works for months, then fails because a column type changed. Pandera catches this early.

### NHS Use Case
```python
import pandera as pa
from pandera import Column, Check, DataFrameSchema

schema = DataFrameSchema({
    "patient_id": Column(pa.String, Check.str_length(equals=10)),
    "department": Column(pa.String, Check.isin(["A&E", "Cardiology", "Surgery"])),
    "wait_time_mins": Column(pa.Int, Check.between(0, 1440)),
    "admission_date": Column(pa.DateTime)
})

# Validate incoming data
validated_df = schema(df)  # Raises error if invalid

# Or in pipeline
@pa.check_input(schema)
def process_patients(df):
    return df.groupby('department').size()
```

### Integration with Great Expectations
- **Great Expectations:** Full data quality platform (covered March 2)
- **Pandera:** Lightweight, Pythonic, schema-focused
- Use both: Pandera for schema, Great Expectations for statistical checks

### Install
```bash
pip install pandera
```

---

## 5. Pyjanitor — Clean Data Cleaning Chains

**What:** Method-chaining extensions for pandas  
**Why it matters:** Cleaner, more readable data cleaning code.

### The Pain
```python
# Old way - hard to read
df = df.rename(columns={'Old Name': 'new_name'})
df = df.dropna(subset=['col1', 'col2'])
df['col1'] = df['col1'].fillna(0)
df = df[df['status'].isin(['active', 'pending'])]
```

### With Pyjanitor
```python
import janitor

df = (
    df
    .rename_columns({'Old Name': 'new_name'})
    .dropna(subset=['col1', 'col2'])
    .fillna(subset=['col1'], value=0)
    .filter_on('status', 'active', 'pending')
)
```

### NHS Use Case
```python
import janitor

df = (
    df
    .clean_names()  # Convert to snake_case
    .remove_empty()  # Drop empty rows/cols
    .encode_categorical('department')  # Optimize for memory
    .flag_missing_values()  # Create _missing columns
)
```

### Install
```bash
pip install pyjanitor
```

---

## Integration: Where These Fit

```
┌─────────────────────────────────────────────────────────┐
│                    DATA SOURCES                          │
│   Supabase (PostgreSQL)    │    CSV/Excel files        │
└──────────────┬──────────────┴──────────────┬─────────────┘
               │                            │
               ▼                            ▼
┌──────────────┴────────────────────────────┴─────────────┐
│                   EDA LAYER                            │
│   ydata-profiling (initial profile)                    │
│   D-Tale (interactive exploration)                     │
└──────────────┬────────────────────────────┬─────────────┘
               │                            │
               ▼                            ▼
┌──────────────┴────────────────────────────┴─────────────┐
│                   VALIDATION LAYER                      │
│   Pandera (schema)          │    Great Expectations    │
│                              │    (statistical checks)  │
└──────────────┬────────────────────────────┬─────────────┘
               │                            │
               ▼                            ▼
┌──────────────┴────────────────────────────┴─────────────┐
│                   PROCESSING                            │
│   Polars (fast ETL)        │    Vaex (huge datasets)   │
└──────────────┬────────────────────────────┬─────────────┘
               │                            │
               ▼                            ▼
┌──────────────┴────────────────────────────┴─────────────┐
│                   OUTPUT                               │
│   Quarto (parameterized reports)                      │
│   Superset (dashboards)                               │
└─────────────────────────────────────────────────────────┘
```

---

## Quick Wins to Try This Week

1. **ydata-profiling:** `pip install ydata-profiling` → run on any CSV
2. **D-Tale:** `pip install dtale` → add to existing notebook
3. **Pandera:** `pip install pandera` → add schema to a pipeline function

---

## Sources

- KDnuggets: "10 Lesser-Known Python Libraries Every Data Scientist Should Be Using in 2026"
- ydata-profiling docs: https://ydata-profiling.readthedocs.io/
- Vaex docs: https://vaex.readthedocs.io/
- D-Tale GitHub: https://github.com/man-group/dtale
- Pandera docs: https://pandera.readthedocs.io/
- Pyjanitor docs: https://pyjanitor-devs.github.io/pyjanitor/
