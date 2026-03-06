# Discovery — 2026-03-06 1800UTC

**Focus:** Python data analysis, SQL optimization, SQL Server drivers

---

## 1. mssql-python: New SQL Server Driver for Python

**URL:** https://github.com/microsoft/mssql-python  
**Status:** GA as of November 2025

Microsoft released a new official Python driver for SQL Server, positioned to replace pyodbc as the default choice. Early benchmarks show better performance and simpler code compared to pyodbc.

**Why it matters for NHS workflow:**
- John uses pyodbc for connecting to NHS SQL Server databases
- mssql-python offers better performance for large result sets
- Simpler authentication handling for Azure AD / Windows Auth
- Direct competitor to pyodbc - worth testing in a pilot

**Install:** `pip install mssql-python`

---

## 2. PyPika: SQL Query Builder for Python

**URL:** https://github.com/kayak/pypika

PyPika is a query builder library that exposes the full richness of SQL through a Pythonic syntax. Unlike ORMs (SQLAlchemy), it stays close to raw SQL while providing programmatic construction.

**Why it matters for NHS workflow:**
- Useful for building complex queries dynamically
- Better than string-concatenation for SQL generation
- Supports advanced SQL features (window functions, CTEs, subqueries)
- Lightweight alternative to full ORM for analytical queries

**Install:** `pip install pypika`

---

## 3. Awesome Data Analysis: Curated Resource List

**URL:** https://github.com/PavelGrigoryevDS/awesome-data-analysis

500+ curated resources covering Python, SQL, Statistics, ML, AI, Visualization. Updated January 2026.

**Why it matters:**
- Comprehensive reference for both beginner and advanced topics
- Includes cheatsheets, roadmaps, and interview prep
- One-stop shop for discovering new tools

---

## Summary

This cycle focused on SQL Server connectivity and query building—areas directly relevant to John's daily NHS work. The **mssql-python** driver is the most actionable discovery: a drop-in replacement for pyodbc with performance benefits worth testing.

---

*Generated: 2026-03-06 18:00 UTC*
