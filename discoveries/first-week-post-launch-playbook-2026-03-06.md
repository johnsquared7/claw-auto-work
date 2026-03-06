# First-Week Post-Launch Playbook — Day 1-7 Action Plan

**Research Date:** 2026-03-06  
**Purpose:** Actionable playbook for days 1-7 after Home Screen Organizer launch

---

## Executive Summary

The first 7 days after launch are critical—apps that gain early momentum are **3x more likely to maintain long-term success**. This playbook provides daily priorities, decision frameworks, and metric thresholds for the Home Screen Organizer launch.

**Key Insight:** The average app loses 77% of daily active users within 3 days. Your goal is to beat this curve through rapid response and authentic engagement.

---

## Day 1: Triage & Confirmation (Launch Day)

### Immediate Actions (First 4 Hours)

| Time Block | Action | Owner |
|------------|--------|-------|
| 0-1 hour | Post to Product Hunt (12:01 AM PT) | Maker |
| 0-1 hour | Share PH link to Twitter/X, Discord, email list | Maker |
| 1-2 hours | Respond to EVERY Product Hunt comment | Maker |
| 2-4 hours | Post TikTok launch video (6-9 PM PT optimal) | Maker |
| Ongoing | War room active in Discord/Slack channel | Team |

### Critical Monitoring

**Server & Stability:**
- [ ] CPU/memory usage within normal limits
- [ ] Database queries running efficiently
- [ ] No 5xx errors in logs
- [ ] Firebase Crashlytics dashboard open

**Analytics Verification:**
- [ ] Sign-up event firing correctly
- [ ] Core action events tracked
- [ ] Attribution links working
- [ ] Supabase dashboard showing real-time data

### Decision Triggers — Day 1

| Metric | Green | Yellow | Red → Action |
|--------|-------|--------|--------------|
| Crash rate | <0.5% | 0.5-2% | >2% → Hotfix within 4 hours |
| App Store rating | 4.5+ | 4.0-4.5 | <4.0 → Review response blitz |
| PH rank | Top 5 | Top 10 | Outside top 10 → Engage network |
| Sign-ups | On target | 50-80% target | <50% → Emergency promo push |

---

## Day 2: Momentum & Response

### Priorities

1. **Product Hunt follow-through**
   - Continue responding to all comments (12:01 AM - 11:59 PM PT)
   - Thank supporters publicly on Twitter
   - Update product based on feedback received

2. **App Store review response**
   - Respond to EVERY review within 4 hours
   - Move troubleshooting conversations offline (email/support)
   - Thank positive reviewers personally

3. **TikTok momentum**
   - Check video performance
   - Reply to comments
   - Consider follow-up video if first performed well

### Checklist — Day 2

- [ ] All PH comments from Day 1 responded to
- [ ] All App Store reviews responded to
- [ ] Server health check (morning + evening)
- [ ] Crash report review — no critical issues?
- [ ] Social media mentions addressed
- [ ] Email to waitlist: "We're live!" follow-up

### Social Media Engagement

**Twitter/X:**
- Quote-tweet supporters with thanks
- Share PH ranking milestone
- Post "Day 1 by the numbers" if strong

**TikTok:**
- Respond to every comment
- Duet/stitch user reactions
- Post behind-the-scenes if momentum builds

---

## Day 3: Stabilization & Iteration

### Priorities

1. **Prepare v1.0.1 hotfix** (if needed)
   - Compile bug reports from reviews/support
   - Prioritize fixes: P0 crashes > P1 broken flows > P2 polish
   - Submit to App Store review (can take 24-48 hours)

2. **User feedback synthesis**
   - Categorize feedback into themes
   - Identify top 3 requested features
   - Document for roadmap

3. **Press follow-up**
   - Send launch recap to journalists who didn't cover
   - Include user numbers if impressive
   - Offer exclusive on v1.1 features

### Metric Check — Day 3

| Metric | Target | If Below Target |
|--------|--------|-----------------|
| D1 Retention | ≥30% | Review onboarding flow |
| D3 Retention | ≥15% | Check value proposition |
| Crash-free rate | ≥99% | Urgent hotfix needed |
| App Store rating | ≥4.5 | Review response surge |

### Community Engagement

- [ ] Discord: Daily update post
- [ ] Reply to all new support tickets within 2 hours
- [ ] Personal outreach to beta testers who haven't converted
- [ ] Thank top contributors publicly

---

## Day 4-5: Optimization & Expansion

### Priorities

1. **ASO quick wins**
   - Review App Store keyword performance
   - A/B test icon if downloads underperforming
   - Update description based on user language

2. **Cross-platform posting**
   - Post TikTok to Instagram Reels
   - Post TikTok to YouTube Shorts
   - Adjust aspect ratio if needed (9:16 universal)

3. **Feature prioritization**
   - Based on feedback synthesis (Day 3)
   - Identify quick wins for v1.1
   - Communicate roadmap to users

### Outreach Actions

| Channel | Action |
|---------|--------|
| Email | Send "Day 3 recap" to power users |
| Twitter | Share "What we learned" thread |
| Reddit | Post in relevant subreddits if not done |
| Discord | Host AMA if community active |

### Metric Thresholds — Day 5

| Metric | Excellent | Good | Needs Attention |
|--------|-----------|------|-----------------|
| D7 Retention | ≥15% | 10-15% | <10% |
| DAU trend | Growing | Stable | Declining |
| App Store rating | 4.5+ | 4.0-4.5 | <4.0 |
| Review response rate | 100% | 80%+ | <80% |

---

## Day 6-7: Reflection & Planning

### Priorities

1. **Week 1 retrospective**
   - What worked? What didn't?
   - Document lessons learned
   - Share publicly (builds trust)

2. **Week 2 planning**
   - Finalize v1.1 scope
   - Schedule content calendar
   - Plan next promotional push

3. **Sustained engagement**
   - Continue daily social presence
   - Maintain review response cadence
   - Keep war room active (reduced hours)

### Week 1 Metrics Summary

Compile into dashboard for John:

| Metric | Week 1 Actual | Target | Status |
|--------|--------------|--------|--------|
| Downloads | TBD | TBD | — |
| D1 Retention | TBD | 30% | — |
| D7 Retention | TBD | 15% | — |
| App Store Rating | TBD | 4.5+ | — |
| Crash-free Rate | TBD | 99%+ | — |
| Review Response Rate | TBD | 100% | — |
| PH Final Rank | TBD | Top 5 | — |
| TikTok Views | TBD | — | — |

---

## Rapid Iteration Decision Framework

### When to Ship Hotfix (v1.0.x)

```
IF crash_rate > 2% AND affecting >100 users:
  → Ship hotfix within 24 hours
  
IF critical_feature_broken AND mentioned in >5 reviews:
  → Ship hotfix within 48 hours
  
IF minor_bug AND easy_fix AND low_risk:
  → Include in v1.1 (not urgent)
```

### When to Prioritize v1.1 Features

```
IF feature_requested_by >10 users AND fits_mvp_scope:
  → Prioritize for v1.1
  
IF feature_blocks_retention AND quick_implement:
  → Prioritize for v1.1
  
IF feature_nice_to_have OR complex:
  → Backlog for v1.2+
```

---

## Escalation Protocols

### P0 — Immediate Action (< 4 hours)
- App crashing for >5% of users
- Security vulnerability discovered
- Data loss occurring
- App Store removal threat

### P1 — Same Day (< 12 hours)
- Critical feature broken
- Payment processing failure
- Major negative press
- Influencer complaint

### P2 — Next Business Day (< 24 hours)
- Minor bug affecting <5% users
- Feature request from key user
- Social media complaint
- Review bomb detected

### P3 — This Week
- UI polish requests
- Minor copy changes
- Nice-to-have features
- Optimization opportunities

---

## Daily Checklist Template

### Morning (9 AM UTC)
- [ ] Check crash reports (Firebase Crashlytics)
- [ ] Review overnight App Store reviews
- [ ] Check server health dashboard
- [ ] Review PH ranking (if still active)
- [ ] Check TikTok/social metrics

### Midday (2 PM UTC)
- [ ] Respond to all new reviews
- [ ] Check support inbox
- [ ] Update team in war room channel
- [ ] Post midday social update

### Evening (8 PM UTC)
- [ ] Final review response push
- [ ] Check DAU numbers
- [ ] Document any incidents
- [ ] Set priorities for next day
- [ ] Update John on status

---

## Key Sources

1. Dogtown Media — "Navigating Your App's First 90 Days Post-Launch" (March 2025)
2. Calmops — "Product Hunt Launch Guide 2026" (March 2026)
3. Enable3.io — "App Retention Benchmarks for 2026" (2026)
4. Engage Coders — "The Ultimate Post-Launch Checklist" (October 2025)
5. GetStream — "2026 Guide to App Retention" (January 2026)
6. Demand Curve — "In-depth Product Hunt launch guide" (December 2023)
7. Multiple sources on retention benchmarks and PH launch strategies

---

## Next Steps

1. **Gate A unblocked** → Proceed with CPP variant launch
2. **Week 1 begins** → Execute this playbook
3. **Daily standups** → Review metrics against thresholds
4. **Weekly retrospective** → Adjust strategy based on learnings

---

_Research by Oracle | 2026-03-06_