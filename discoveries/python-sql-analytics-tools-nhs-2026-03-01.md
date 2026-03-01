# Discovery: High-Performance Python & SQL Tools for Analytics Workflows

**Date:** 2026-03-01  
**Category:** Data Analysis / SQL Optimization  
**Quality:** Targeted for NHS/Healthcare analyst workflows

---

## TL;DR

Three categories of tools that could significantly speed up John's NHS reporting pipelines:
1. **Polars** - 10-100x faster than pandas for large dataset processing
2. **DuckDB** - Run SQL queries directly on CSV/Parquet files without loading into a database
3. **EverSQL** - AI-powered query optimization for PostgreSQL/MySQL

---

## 1. Polars — The Fast Pandas Alternative

**What:** Rust-based DataFrame library with pandas-like API but parallel execution  
**Why it matters:** Pandas uses only 1 CPU core. Polars uses all cores automatically.

### Benchmark (from Chengzhi Zhao's analysis on 10.8M row NYC Parking dataset):

| Operation | Pandas | Polars | Speedup |
|-----------|--------|--------|---------|
| Filter | 0.42s | ~0.05s | **8x** |
| GroupBy | 0.60s | ~0.04s | **15x** |
| Self-Join | 4.16s | ~0.12s | **35x** |
| Window Function | 17.47s | ~0.30s | **58x** |

### NHS Use Case
If John is processing monthly patient activity reports with millions of rows, Polars could cut processing time from ~20 minutes to under 1 minute.

**Getting started:**
```python
import polars as pl
df = pl.read_csv("monthly_activity.csv")
result = df.group_by("department").agg(pl.col("patient_id").n_unique())
```

**Note:** Polars has a pandas compatibility layer (`polars.convert.from_pandas`) if gradual migration is preferred.

---

## 2. DuckDB — SQL on Files, No Database Required

**What:** In-process SQL OLAP database that reads CSV, Parquet, JSON directly  
**Why it matters:** No ETL needed. Just point DuckDB at files and write SQL.

### Why It's Different from SQLite
- SQLite is OLTP (transactional). DuckDB is OLAP (analytics).
- Optimized for aggregations, joins, window functions on large datasets
- Can query 100GB+ files without loading into memory

### NHS Use Case
```sql
-- Query patient data directly from CSV without importing to PostgreSQL
SELECT 
    department,
    COUNT(DISTINCT patient_id) as unique_patients,
    AVG(wait_time_minutes) as avg_wait
FROM read_csv_auto('weekly_activity.csv')
WHERE admission_date >= '2026-01-01'
GROUP BY department
ORDER BY unique_patients DESC;
```

**Python integration:**
```python
import duckdb
con = duckdb.connect()
result = con.execute("SELECT * FROM read_csv_auto('data.csv') WHERE dept = 'A&E'").df()
```

### Key Feature: Pandas Integration
DuckDB can convert query results to pandas DataFrames instantly:
```python
df = con.execute("SELECT * FROM df WHERE col > 100").df()
```

---

## 3. EverSQL — AI-Powered SQL Optimization

**What:** Automatic query optimization for PostgreSQL and MySQL  
**Cost:** Free tier available; paid plans from $29/month

### Features:
- Analyzes query execution plans
- Automatically suggests index changes
- Rewrites queries for better performance
- Provides explanations of what changed and why

### NHS Use Case
If John's Supabase (PostgreSQL) queries are slow, EverSQL can:
1. Analyze slow queries from query logs
2. Suggest composite indexes (e.g., `(department, admission_date, status)`)
3. Rewrite complex JOINs with better execution plans

### Example Optimization
```sql
-- Before (slow)
SELECT * FROM appointments a
JOIN patients p ON a.patient_id = p.id
WHERE p.postcode LIKE 'SW%' AND a.status = 'completed';

-- After (EverSQL might suggest)
-- Add index: CREATE INDEX idx_patient_postcode ON patients(postcode);
-- Add index: CREATE INDEX idx_appointment_status_patient ON appointments(status, patient_id);
```

---

## 4. Additional Finds Worth Monitoring

### cuDF (NVIDIA)
- GPU-accelerated DataFrames
- Best for teams with NVIDIA GPUs
- Pandas-compatible API
- **NHS use case:** If processing massive datasets on a GPU-enabled workstation

### PawSQL
- Open-source SQL optimizer
- Index analysis (used/not used/missing indexes)
- Works with PostgreSQL, MySQL, Oracle
- **Link:** https://github.com/pawsql

### Aiven AI Optimiser
- Real-time query monitoring
- Automated indexing recommendations
- 24/7 performance alerts

---

## Recommendation for John

**Start with Polars** — it's the lowest-friction upgrade:
1. Install: `pip install polars`
2. Replace `import pandas as pd` → `import polars as pl`
3. Most common operations have direct equivalents

**Then try DuckDB** for ad-hoc SQL queries on exported files — no database setup needed.

**Use EverSQL** if specific Supabase queries are problematic — free tier should cover basic needs.

---

## Sources

- Chengzhi Zhao: "4 Faster Pandas Alternatives for Data Analysis" (June 2025)
- KDnuggets: "10 Lesser-Known Python Libraries Every Data Scientist Should Be Using in 2026"
- EverSQL website and documentation
- h2oai/db-benchmark
