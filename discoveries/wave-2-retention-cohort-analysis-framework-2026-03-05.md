# Wave 2: Retention Cohort Analysis Framework

**Created:** 2026-03-05  
**Owner:** Oracle  
**For:** Vector (SQL) + Beacon (dashboard)

---

## 1. Cohort Bucket Definitions

| Bucket | Definition | Use Case |
|--------|------------|----------|
| **D1** | Users active Day 1 after install | Early activation signal |
| **D7** | Users active Day 7 after install | Week 1 retention |
| **D30** | Users active Day 30 after install | Month 1 retention |
| **Weekly** | Users active in same week as install | B2C apps (default) |
| **Monthly** | Users active in same month as install | B2B/SaaS apps |

**Recommendation:** Use **weekly cohorts** for Home Screen Organizer (B2C utility app).

---

## 2. Key Retention Metrics to Track

1. **Classic Retention** — % of users who return on/after N days
2. **Rolling Retention** — % of users who return *at least once* after N days
3. **Bracket Retention** — Users active in specific time windows (e.g., Days 2-7)
4. **Session Depth** — Avg sessions per returning user
5. **Feature Adoption** — Which features drive retention

---

## 3. SQL Templates (PostgreSQL/Supabase)

### Template A: Weekly Cohort Retention

```sql
-- Step 1: Bucket users into weekly cohorts by first_active_date
WITH cohort_weeks AS (
  SELECT 
    user_id,
    DATE_TRUNC('week', MIN(created_at))::date AS cohort_week
  FROM app_events
  GROUP BY user_id
),

-- Step 2: Calculate weeks since cohort start for each activity
user_activity_weeks AS (
  SELECT 
    e.user_id,
    DATE_TRUNC('week', e.created_at)::date AS activity_week,
    c.cohort_week,
    EXTRACT(WEEK FROM e.created_at - c.cohort_week)::int AS weeks_since
  FROM app_events e
  JOIN cohort_weeks c ON e.user_id = c.user_id
),

-- Step 3: Get unique users per cohort per week
retention_base AS (
  SELECT 
    cohort_week,
    weeks_since,
    COUNT(DISTINCT user_id) AS active_users
  FROM user_activity_weeks
  WHERE weeks_since >= 0
  GROUP BY cohort_week, weeks_since
),

-- Step 4: Get cohort sizes
cohort_sizes AS (
  SELECT 
    cohort_week,
    COUNT(DISTINCT user_id) AS cohort_size
  FROM cohort_weeks
  GROUP BY cohort_week
)

-- Final: Retention percentages
SELECT 
  r.cohort_week,
  s.cohort_size,
  r.weeks_since,
  r.active_users,
  ROUND(r.active_users::numeric / s.cohort_size * 100, 2) AS retention_pct
FROM retention_base r
JOIN cohort_sizes s ON r.cohort_week = s.cohort_week
ORDER BY r.cohort_week, r.weeks_since;
```

### Template B: D1/D7/D30 Quick Query

```sql
SELECT 
  DATE_TRUNC('day', created_at)::date AS install_date,
  COUNT(*) AS total_installs,
  COUNT(DISTINCT CASE WHEN days_active >= 1 THEN user_id END) AS d1_retention,
  COUNT(DISTINCT CASE WHEN days_active >= 7 THEN user_id END) AS d7_retention,
  COUNT(DISTINCT CASE WHEN days_active >= 30 THEN user_id END) AS d30_retention
FROM (
  SELECT 
    user_id,
    created_at,
    MAX(EXTRACT(DAY FROM event_date - created_at)) AS days_active
  FROM app_events
  GROUP BY user_id, created_at::date
) sub
GROUP BY DATE_TRUNC('day', created_at)::date
ORDER BY install_date DESC;
```

---

## 4. Interpreting Results

| Retention Rate | Interpretation | Action |
|----------------|----------------|--------|
| D1 < 20% | Poor activation | Improve onboarding, first-run UX |
| D7 < 10% | Weak stickiness | Add reminder notifications, widgets |
| D30 < 5% | Churn problem | Re-engage campaigns, feature discovery |
| D7 > 30% | Healthy | Maintain, optimize new user flow |
| Curve flattens at W4+ | Product-market fit signal | Scale acquisition |

**Benchmark (utility apps):** D1: 25-40%, D7: 10-20%, D30: 5-10%

---

## 5. Implementation Notes

- **Event needed:** `app_opened` or any engagement event as "active" signal
- **Cohort key:** Use `first_seen_at` (first app open) not signup date
- **Update cadence:** Daily for recent cohorts, weekly for historical
- **Slice by:** Country, source (organic/paid), device type

---

## 6. Sources

1. Holistics — "Calculate Cohort Retention Analysis with SQL" (2020)
2. Sisense — "How to Calculate Cohort Retention in SQL" (2025)
3. Lenny's Newsletter — "How to measure cohort retention" (2022)
4. Galaxy — "Retention Cohorts with SQL Best Practices" (2025)
5. Periscope Data — "SQL-Based Approach to Cohort Retention"
