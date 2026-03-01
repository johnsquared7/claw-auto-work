# Discovery File — 2026-03-01

*Autonomous discovery cycle for John's NHS analyst workflow*

---

## 1. SQL Server Performance for Healthcare Systems

**Source:** Medium (Feb 2026)  
**URL:** https://medium.com/@srikanth5b9/sql-server-performance-optimization-for-healthcare-systems-a-practical-guide-1a1df70a0c7b

**Why it's interesting:**
- Practical guide specifically for healthcare SQL
- Partition elimination can reduce data scanned by 90%+
- Recent data (most frequently accessed) isolated in smaller partitions
- Queries for last 30 days see massive speedups

**Relevance to John:** Directly applicable to NHS data queries — date-based partitions are common in patient records.

---

## 2. Database Health Monitor — Free SQL Performance Tool

**Source:** databasehealth.com  
**URL:** https://databasehealth.com/

**Why it's interesting:**
- Free download for SQL Server monitoring
- Tracks query performance, index health, blocking
- No expensive enterprise license needed

**Relevance to John:** Low-cost option for monitoring NHS SQL Server performance without additional spend.

---

## 3. Streamlit vs Dash — 2026 Framework Comparison

**Source:** Kanaries (Feb 2026)  
**URL:** https://docs.kanaries.net/topics/Streamlit/streamlit-vs-dash

**Key findings:**
| Factor | Streamlit | Dash |
|--------|-----------|------|
| Ease of use | ✅ Easier | steeper learning curve |
| Scaling | Struggles over 50 users | ✅ Better scaling |
| Customization | Limited | ✅ React-based |
| Best for | Quick internal apps | Production data apps |

**Relevance to John:** For Python viz/reporting — Streamlit is fastest for prototyping, but Dash better if multiple users need access.

---

## 4. NHS Healthcare Analysis Python Package

**Source:** GitHub Topics  
**URL:** https://github.com/topics/healthcare-analysis

**Why it's interesting:**
- Contains Python functions specifically for rectifying common NHS data issues
- Uses pandas, dask-modelling for large datasets
- Open source — free to use

**Relevance to John:** Potential library for NHS-specific data cleaning/analysis patterns.

---

## 5. i2b2 Query Tool — Clinical Research SQL Interface

**Source:** PMC (NIH)  
**URL:** https://pmc.ncbi.nlm.nih.gov/articles/PMC9306316/

**Why it's interesting:**
- GUI-based SQL query builder for clinical data
- Used in hospitals worldwide for cohort identification
- No SQL knowledge required for basic queries

**Relevance to John:** Could be useful for non-technical staff to build queries, or as a model for building NHS-facing query interfaces.

---

## Quick Recommendations

1. **Start with Streamlit** for quick Python dashboard prototypes — fast to build
2. **Look into partitioning** for large NHS date-based tables (90%+ performance gain)
3. **Try Database Health Monitor** before investing in paid SQL monitoring
4. **Check the NHS healthcare-analysis GitHub** topic for reusable patterns

---

*Discovery cycle completed: 2026-03-01 02:00 UTC*
