# Discovery: NHS DART Open Analytics Template & Projects

**Date:** 2026-03-04  
**Category:** NHS Analytics / Reporting / Templates  
**Quality:** High — Official NHS England resources, directly applicable to John's workflow

---

## TL;DR

3 discoveries for John's NHS analyst workflow:
1. **NHS DART Open Analytics Template** — NHS.UK themed template for automated reports
2. **SynPath** — Generate synthetic patient data in FHIR format for testing
3. **Time Series Forecasting** — Prophet/SARIMA templates for NHS data

---

## 1. NHS DART Open Analytics Template — Branded NHS Reports

**Repo:** https://github.com/nhsx/open-analytics-template  
**Demo:** https://nhsx.github.io/open-analytics-template/

**What:** Official NHS.UK themed template for building open analytics projects with Python, Plotly, GitHub Pages, and GitHub Actions.

### Key Features:
- Pre-built NHS branding (NHS.UK style)
- End-to-end analytical tool template
- GitHub Actions for automated reports
- Plotly for interactive charts

### Why It Matters for John:
- **Instant NHS-branded reports** — No need to style from scratch
- **Automated publishing** — GitHub Actions runs on schedule
- **Interactive dashboards** — Plotly-powered, works in browser

### Quick Start:
```bash
# Clone the template
git clone https://github.com/nhsx/open-analytics-template.git
cd open-analytics-template

# Customize for your data
# Edit config.yaml and data files
# Deploy to GitHub Pages
```

### Components:
- `config.yaml` — Data source configuration
- `.github/workflows/` — Automated report generation
- `python/` — Analysis scripts
- `assets/` — NHS.UK styling

---

## 2. SynPath — Synthetic Patient Data Generator

**Repo:** https://github.com/nhsx/SynPath

**What:** Generate synthetic electronic health records in **FHIR v4 format** using agent-based modeling to simulate patient pathways.

### Why It Matters:
- **Safe testing data** — No privacy concerns with real patient data
- **FHIR format** — Interoperable with modern NHS systems
- **Realistic pathways** — Simulates actual patient journeys

### Use Cases:
- Test report pipelines without exposing real data
- Train analysts on realistic synthetic datasets
- Demo dashboards without sensitive information

### Related: SynPath Diabetes
**Repo:** https://github.com/nhsx/SynPath_Diabetes  
Type 2 diabetes pathway simulation module

---

## 3. Time Series Forecasting for NHS Data

**Repo:** https://github.com/nhsx/Time_Series_Forecasting_MS

**What:** Comparative forecasting templates using **Prophet** and **SARIMA** for NHS data.

### What's Included:
- Base starting code for forecasting
- Prophet integration (Facebook's time series tool)
- SARIMA models for seasonal data
- Comparative analysis framework

### NHS Use Cases:
- **Bed occupancy forecasting** — Predict demand
- **A&E waiting times** — Trend analysis  
- **Appointment scheduling** — Seasonal patterns
- **Equipment/maintenance** — Predictive scheduling

### Example (Prophet):
```python
from prophet import Prophet
import pandas as pd

# Prepare data (date, value columns)
df = pd.read_csv('bed_occupancy.csv')

model = Prophet(yearly_seasonality=True, weekly_seasonality=True)
model.fit(df)

# Forecast next 30 days
future = model.make_future_dataframe(periods=30)
forecast = model.predict(future)
```

---

## Other Notable NHS DART Projects

| Project | Description | Tech |
|---------|-------------|------|
| [AIF Allocation Tool](https://github.com/nhsx/AIF_Allocation_Tool) | Streamlit tool for need-based allocations | Streamlit/Python |
| [GP Mapping](https://nhsx.github.io/gp_mapping/) | Patient registration mapping | Python/Folium |
| [Antibiotic Cost](https://nhsx.github.io/antibiotic_cost/) | Prescribing cost visualization | Plotly |
| [Privacy Fingerprint](https://github.com/nhsx/PrivacyFingerprint) | Identify sensitive elements in text | NLP |
| [System Hierarchies](https://github.com/nhsx/SystemHierarchies) | NHS organisation structure mapping | Python |

---

## Quick Reference

### Install Commands
```bash
# Forecasting
pip install prophet pandas plotly

# Mapping
pip install folium geopandas

# FHIR (for SynPath)
pip install fhir.resources
```

### Key Links
- **NHS DART Projects:** https://nhsx.github.io/AnalyticsUnit/projects.html
- **Open Analytics Template:** https://nhsx.github.io/open-analytics-template/
- **NHS Python Community:** https://nhs-pycom.net/

---

## Next Steps for John

1. **Start with the Open Analytics Template** — Clone it, swap in your data, deploy
2. **Try SynPath** — Generate synthetic test data for your pipelines
3. **Apply Prophet** — Forecast bed occupancy or A&E waiting times

---

*Generated: 2026-03-04 18:00 UTC*
*Focus: NHS DART resources, branded reporting templates, time series forecasting*
