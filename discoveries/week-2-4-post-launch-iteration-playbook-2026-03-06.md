# Week 2-4 Post-Launch Iteration Playbook

**Created:** 2026-03-06
**Author:** Oracle (Research Agent)
**Purpose:** Guide for Home Screen Organizer app iteration in weeks 2-4 post-launch

---

## Executive Summary

The first 4 weeks after launch are critical for establishing product-market fit. Apps that iterate effectively in this window see 3x higher retention at Day 30. This playbook provides decision frameworks, timing guidelines, and prioritization matrices for rapid iteration.

---

## Week-by-Week Framework

### Week 2: Stabilization & Data Collection

**Focus:** Fix what's broken, gather what's needed

**Priorities:**
1. **P0 Bug Fixes** - Any crash-inducing bugs or major UX blockers
2. **Review Response** - Continue daily review monitoring and response
3. **Data Analysis** - First full week of metrics available
4. **Feedback Categorization** - Organize all user feedback into taxonomy

**Actions:**
| Day | Focus | Output |
|-----|-------|--------|
| Day 8 | Crash analysis + P0 fixes | Hotfix if crash rate >0.5% |
| Day 9 | Feedback categorization | Feature request backlog |
| Day 10 | Usage pattern analysis | Drop-off map |
| Day 11 | Review sentiment analysis | Common complaint themes |
| Day 12 | First week metrics review | Week 1 report |
| Day 13 | v1.0.1 planning | Patch notes draft |
| Day 14 | v1.0.1 submission (if needed) | App Store update |

**Key Metrics to Track:**
- Crash-free rate: Target ≥99.85%
- D7 retention: Target ≥15%
- Average rating: Target ≥4.3
- Top feature requests by frequency

---

### Week 3: First Feature Decisions

**Focus:** Prioritize and plan v1.1

**Priorities:**
1. **Feature Prioritization** - Use RICE or Value/Effort matrix
2. **Quick Wins** - Low-effort, high-impact improvements
3. **User Communication** - "We heard you" updates
4. **Roadmap Draft** - v1.1, v1.2 scope

**Feature Request Triage Framework:**

```
Impact Score = (Users Affected × Severity × Strategic Fit)
Effort Score = (Dev Days × Complexity × Risk)
Priority = Impact Score / Effort Score
```

**Triage Categories:**
| Category | Criteria | Timeline |
|----------|----------|----------|
| P0 - Critical | Affects >20% users or crashes | Immediate |
| P1 - High | Frequent request, low effort | Week 3-4 |
| P2 - Medium | High value, medium effort | Week 5-6 |
| P3 - Low | Nice to have, backlog | Future sprint |
| P4 - Won't Do | Misaligned with vision | Decline |

**Actions:**
| Day | Focus | Output |
|-----|-------|--------|
| Day 15 | Feature request analysis | Prioritized backlog |
| Day 16 | Quick win identification | 3-5 candidates |
| Day 17 | v1.1 scope decision | Feature list |
| Day 18 | Design review (if needed) | Mockups |
| Day 19 | Development kickoff | Sprint start |
| Day 20-21 | Development + testing | v1.1 progress |

---

### Week 4: Iteration Execution

**Focus:** Ship v1.1 or v1.0.2, prepare for sustained rhythm

**Priorities:**
1. **Ship Update** - v1.1 or patch release
2. **Communicate Changes** - Update notes, social posts
3. **Process Documentation** - Establish iteration rhythm
4. **Metrics Dashboard** - Automate tracking

**App Store Update Timing:**
- **Best days:** Tuesday-Thursday
- **Avoid:** Friday-Monday (weekend review delays)
- **Review time buffer:** 24-48 hours for App Store review
- **Update frequency:** Minor releases every 2-4 weeks recommended

**Update Messaging Template:**
```
Version X.X.X

✨ NEW: [Feature 1 - one line benefit]
🔧 FIXED: [Bug fixes - max 3 items]
⚡ IMPROVED: [Performance/UX improvements]

Thanks for your feedback! [Specific callout: "You asked, we listened"]
```

**Actions:**
| Day | Focus | Output |
|-----|-------|--------|
| Day 22 | v1.1 final testing | QA sign-off |
| Day 23 | v1.1 submission | App Store review |
| Day 24 | Update notes + social prep | Announcement ready |
| Day 25 | Launch v1.1 | Update live |
| Day 26 | Monitor metrics | Performance check |
| Day 27 | User communication | Social posts |
| Day 28 | Month 1 retrospective | Lessons learned |

---

## Decision Frameworks

### Bug vs Feature Decision Tree

```
Is it blocking users?
├── YES → P0 Bug Fix (immediate)
└── NO → Is it causing frustration?
    ├── YES → Is fix < 4 hours?
    │   ├── YES → Include in next release
    │   └── NO → Prioritize against features
    └── NO → Is it cosmetic?
        ├── YES → Backlog
        └── NO → Monitor frequency
```

### Hotfix vs Scheduled Release Decision

| Criteria | Hotfix | Scheduled Release |
|----------|--------|-------------------|
| Crash rate | >1% | <1% |
| Users affected | >10% | <10% |
| Workaround exists | No | Yes |
| Fix complexity | Simple | Complex |
| Time to fix | <24 hours | >24 hours |

### Feature Prioritization: RICE Method

**RICE Score = (Reach × Impact × Confidence) / Effort**

| Factor | Scale | Description |
|--------|-------|-------------|
| Reach | Users/quarter | How many will use this? |
| Impact | 0.25-3 | 0.25=minimal, 1=medium, 3=massive |
| Confidence | 0.5-1.0 | How sure are you? |
| Effort | Person-months | Total dev time needed |

**Example Scoring:**
| Feature | Reach | Impact | Confidence | Effort | RICE |
|---------|-------|--------|------------|--------|------|
| Dark mode | 5000 | 1 | 0.8 | 0.5 | 8000 |
| Widget customization | 3000 | 2 | 0.7 | 1.0 | 4200 |
| iPad support | 500 | 3 | 0.9 | 2.0 | 675 |

---

## Balance Framework: Bugs vs Features

### The 70/20/10 Rule

| Category | Allocation | Rationale |
|----------|------------|-----------|
| Stability & Bugs | 70% | Trust is foundation |
| Feature Improvements | 20% | User-requested enhancements |
| New Features | 10% | Strategic bets |

### Adjusted by App Stage

| App Stage | Bugs | Improvements | New Features |
|-----------|------|--------------|--------------|
| Week 2-4 | 80% | 15% | 5% |
| Month 2-3 | 60% | 25% | 15% |
| Month 4+ | 40% | 35% | 25% |

---

## Iteration Rhythm

### Recommended Cadence

| Activity | Frequency | Owner |
|----------|-----------|-------|
| Crash monitoring | Daily | Dev |
| Review monitoring | Daily | Support |
| Metrics review | Weekly | PM |
| User feedback analysis | Weekly | PM |
| Feature prioritization | Bi-weekly | PM + Lead |
| Sprint planning | Bi-weekly | Team |
| Retrospective | Monthly | Team |

### Sprint Structure (2-week sprints)

```
Week 1: Design → Dev → Dev
Week 2: Dev → Dev → Test → Ship
```

---

## Communication Templates

### User Feedback Response (Feature Request)

> Thanks for the suggestion! We've added this to our feature backlog. Can't promise a timeline, but we review all requests during our regular prioritization. Appreciate you taking the time to share!

### Update Announcement (Social)

> 🚀 v1.1 is live!
> 
> Based on your feedback:
> ✨ [Feature 1]
> 🔧 [Fix 1]
> ⚡ [Improvement 1]
> 
> Keep the feedback coming! We're listening.

### Monthly Update (Newsletter/Discord)

> **Month 1 Recap**
> 
> 📊 [X] downloads, [Y] rating
> 🐛 Fixed [Z] bugs
> ✨ Shipped [A, B, C] features
> 🗺️ Coming next: [D, E]
> 
> Thanks for being an early supporter!

---

## Success Metrics

### Week 4 Checkpoint Targets

| Metric | Target | Stretch |
|--------|--------|---------|
| D30 retention | ≥10% | ≥15% |
| App Store rating | ≥4.3 | ≥4.5 |
| Crash-free rate | ≥99.5% | ≥99.9% |
| Feature adoption (new) | ≥20% | ≥40% |
| Support ticket volume | Decreasing | Stable or ↓ |

### Health Indicators

🟢 **Green:** On track for v1.2
🟡 **Yellow:** Needs attention, adjust priorities
🔴 **Red:** Critical issue, pause new features

---

## Sources

1. Kernelics - Post-Launch Mobile App Optimization (2025)
2. MVP App Development - 7 Steps to Mastering Rapid Iteration (2025)
3. Userpilot - 15 Feature Prioritization Frameworks (2026)
4. mAccelelerator - Iterative Feedback Loops (2025)
5. Reddit r/ProductManagement - Feature Prioritization Discussion (2024)

---

_Oracle Research Deliverable - Task j9756zvgzavkpycz96hcxny6w582dmwh_