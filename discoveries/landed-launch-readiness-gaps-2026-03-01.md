# Launch Readiness Gaps — 2026-03-01

## Gate Status Summary

| Gate | Status | Details |
|------|--------|---------|
| A — Creative/Distribution | ✅ PASS | All items checked |
| B — Tracking Integrity | ✅ PASS | All items checked |
| C — Dry Run Validation | ❌ FAIL | 4/5 events NOT wired in app code |
| D — Experiment Governance | ⚠️ PARTIAL | Scorecard owner not assigned |

---

## Critical Blocker: Gate C — Event Wiring

**Status:** Analytics infrastructure ready (service + migration), but **NOT WIRED in app code**.

### Missing Event Calls

| Event | Status | Action Required |
|-------|--------|------------------|
| `acq_session_started` | ❌ NOT WIRED | Add call in app entry/linking handler |
| `store_view` | ❌ NOT WIRED | Add call when CPP/store listing rendered |
| `install_attributed` | ❌ NOT WIRED | Add call when install attribution confirmed |
| `app_first_open` | ❌ NOT WIRED | Add call on first app open after install |
| `first_value_reached` | ✅ WIRED | Added 2026-02-27 in AppBottomSheet |

**⚠️ NO-LAUNCH until all 4 events are wired.**

---

## Gate D Gap

- **Weekly scorecard owner** — Not assigned. Needs human assignment.

---

## Recommendation

1. **Immediate:** Assign Gate C event wiring to Artisan (technical)
2. **Immediate:** Assign scorecard owner (can be John or delegated)
3. **After wiring:** Run dry-run validation per bucket
4. **Then:** Re-review gates for GO decision

---

## Sources
- `knowledge/landed-wave1-launch-readiness-gate-v1-2026-02-19.md`
- `landed-app/lib/analytics.ts`
