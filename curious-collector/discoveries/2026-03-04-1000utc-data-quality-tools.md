# Discovery: Data Quality Tools for NHS Analyst Workflow
**Date:** 2026-03-04
**Time:** 1000 UTC
**Source:** Autonomous discovery cycle
**Focus:** Data quality testing, validation frameworks, healthcare data integrity

---

## 🔥 Great Expectations (GX Core) - Data Quality Framework

**What:** Open-source Python framework for validating and documenting data quality  
**Why interesting:** Critical for NHS - ensures patient data meets quality standards before reporting  
**Key features:**
- Define "expectations" - tests for what valid data should look like
- Automatic data profiling from CSV/SQL
- Generates HTML data documentation automatically
- Integrates with pandas, Spark, SQL databases
- CI/CD integration for automated validation

**Use case for NHS:**
```python
import great_expectations as gx

# Define expectation for NHS number
expectation_suite = gx.get_expectation_suite(
    expectation_suite_name="nhs_patient_data"
)
df.expect_column_values_to_be_of_type("nhs_number", "str")
df.expect_column_values_to_match_regex("nhs_number", "^\d{10}$")

# Validate and get results
results = df.validate(expectation_suite=expectation_suite)
```

**Website:** greatexpectations.io/gx-core  
**Open source:** github.com/great-expectations/great_expectations

---

## 🔥 Soda Core - SQL-Native Data Quality

**What:** Lightweight data quality checks written in YAML + SQL  
**Why interesting:** More approachable than Great Expectations for SQL-first analysts  
**Key features:**
- Checks defined in simple YAML files
- Custom SQL checks for complex validation
- Fast setup, no Python coding required for basic use
- Supports 30+ data sources (PostgreSQL, MySQL, Snowflake, etc.)
- Programmatic Python API for automation

**Comparison to Great Expectations:**
| Aspect | Great Expectations | Soda Core |
|--------|-------------------|-----------|
| Setup | More complex | Simpler |
| SQL integration | Limited | Native |
| Custom checks | Python UDFs | SQL queries |
| Best for | Complex validation pipelines | Quick quality checks |

**Use case for NHS:**
```yaml
# soda_checks/nhs_referrals.yml
checks for table nhs_referrals:
  - row_count > 0
  - values in referral_date must be between '2024-01-01' and today
  - values in nhs_number must match_regex: "^[0-9]{10}$"
  - missing_count(referral_source) < 5
```

**Website:** soda.io/core  
**Install:** `pip install soda-core`

---

## 📊 Why Data Quality Matters for NHS

**Healthcare data challenges:**
- Missing or invalid NHS numbers
- Duplicate patient records
- Date inconsistencies across systems
- Incomplete referral data
- Schema drift from system updates

**Impact:**
- Incorrect performance metrics
- Failed regulatory reports
- Patient safety risks
- Audit failures

**Solution:** Automated data quality checks catch issues before they reach dashboards and board reports.

---

## 🔧 Implementation Path for John

**Phase 1: Quick Wins (This Week)**
1. Install Soda Core: `pip install soda-core-postgres`
2. Create basic YAML checks for existing SQL queries
3. Run checks alongside daily report generation

**Phase 2: Foundation (This Month)**
1. Set up Great Expectations for critical NHS datasets
2. Generate automatic data documentation
3. Add validation to any Python ETL scripts

**Phase 3: Automation (Quarter)**
1. Integrate into CI/CD pipeline
2. Add alerts for failed checks
3. Build data quality dashboard

---

## 📌 Saved Links

- https://greatexpectations.io/gx-core - Great Expectations GX Core
- https://github.com/great-expectations/great_expectations - GitHub repo
- https://soda.io/core - Soda Core
- https://www.thedataletter.com/p/tool-review-soda-core-vs-great-expectations - Comparison article
- https://atlan.com/open-source-data-quality-tools/ - 2026 landscape

---

*Discovery cycle complete - 1000 UTC*
*Quality: Specific data quality tools with NHS relevance. Both open-source, both actionable.*
