# Wave 2 Research: Retention Cohort Analysis

**Oracle | March 4, 2026 | Priority: P1**

---

## Executive Summary

Retention is the single strongest indicator of product-market fit. For Home Screen Organizer apps, expected benchmarks are D1: 25-30%, D7: 10-15%, D30: 5-7%. Utility/productivity apps perform slightly above average. Key insight: if users stay past Day 30, they're likely to stay long-term — focus resources on early activation.

---

## 2026 Mobile App Retention Benchmarks

### Overall Average (All Apps)
| Metric | Benchmark |
|--------|-----------|
| D1 Retention | 25-30% |
| D7 Retention | 10-15% |
| D30 Retention | 5-7% |

Source: Sendbird, UXCam, Adjust (2025-2026)

### By Category

| Category | D1 | D7 | D30 |
|----------|-----|-----|------|
| Fintech | 30.3% | 12-15% | 6-8% |
| Health & Fitness | 30-35% | 15-18% | 8-10% |
| Productivity | 28-32% | 14-18% | 7-10% |
| Social Media | 26.3% | 10-12% | 5-7% |
| Gaming | 28-33% | 8-12% | 4-6% |
| Dating | 26-28% | <10% | 3-5% |

### Android Launcher/App Specific
- Day 1: ~21.1%
- Day 30: ~2.1%

*Note: Launcher/customization apps tend to have lower long-term retention due to "set and forget" behavior — users configure once and don't return.*

---

## Cohort Segmentation by User Source

### Typical Patterns by Channel

| Acquisition Channel | D1 | D7 | D30 | Notes |
|---------------------|-----|-----|------|-------|
| Paid (Apple Search Ads) | 20-25% | 8-12% | 3-5% | High intent but low loyalty |
| Organic (App Store Browse) | 30-35% | 15-20% | 8-12% | Better quality, self-selected |
| Referral | 35-40% | 18-22% | 10-15% | Highest trust, best retention |
| Social/Influencer | 22-28% | 10-14% | 4-7% | Variable quality |

**Key Insight**: "Borrowed trust" channels (referral, organic) outperform paid acquisition 2-3x on retention. Prioritize SEO, App Store optimization, and referral programs over paid UA.

---

## Patterns That Predict Churn vs Loyalty

### Churn Predictors (Red Flags)
1. **No core action in first 3 minutes** — users who don't experience "aha moment" quickly churn
2. **Permission fatigue** — excessive permission requests upfront = 40% higher Day 1 churn
3. **No push notification opt-in** — 3x lower re-engagement
4. **No return trigger** — no scheduled reminders, widgets, or notifications to bring users back
5. **No progress/saving** — if users feel their setup isn't "stored," they abandon

### Loyalty Drivers (Green Flags)
1. **Immediate value delivery** — skip tutorials, let users start organizing immediately
2. **Widget on home screen = daily touchpoint** — leverage widget API for re-engagement
3. **Streak/gamification** — "Organization score" encourages return visits
4. **Cloud sync** — creates switching cost, reduces uninstall
5. **Personalization** — themes, icon packs, customization = emotional investment

---

## Retention Tactics from Successful Launcher Apps

### Top 10 Tactics (Ranked by Impact)

1. **Widget-first onboarding** (Impact: High)
   - Place widget during setup, creates daily visibility
   
2. **Progress persistence** (Impact: High)
   - Auto-save layout, assure users their work isn't lost

3. **Quick actions from widget** (Impact: High)
   - One-tap reorganize without opening app

4. **Push notifications for "beautify your screen"** (Impact: Medium)
   - Seasonal themes, new icon packs

5. **In-app feedback loop** (Impact: Medium)
   - "How's your home screen?" survey at D3, D7

6. **Referral program with customization rewards** (Impact: Medium)
   - "Invite a friend, unlock premium icons"

7. **Streak tracking for organization** (Impact: Medium)
   - "You've organized 7 days in a row!"

8. **Weekly wallpaper/suggestion push** (Impact: Medium-Low)
   - AI suggests improvements

9. **App Store rating prompt at D7** (Impact: Low)
   - Only for engaged users (not D1 churn)

10. **Early subscriber win-back** (Impact: Low)
    - If user skips sub, offer limited trial

---

## Implementation Recommendations

### For Landed / Home Screen Organizer

| Tactic | Effort | Priority |
|--------|--------|----------|
| Widget with quick actions | High | P1 |
| Auto-save layout to cloud | Medium | P1 |
| D3 feedback prompt | Low | P2 |
| Streak/points system | Medium | P2 |
| Referral with rewards | Medium | P2 |
| Push notification strategy | Low | P2 |

### Target Benchmarks (Ambitious)

- D1: 35% (above average — strong onboarding)
- D7: 18% (above average — widget re-engagement)
- D30: 10% (above average — loyalty mechanics)

---

## Sources (12)

1. https://www.plotline.so/blog/retention-rates-mobile-apps-by-industry
2. https://enable3.io/blog/app-retention-benchmarks-2025
3. https://sendbird.com/blog/app-retention-benchmarks-broken-down-by-industry
4. https://uxcam.com/blog/mobile-app-retention-benchmarks/
5. https://www.adjust.com/resources/guides/user-retention/
6. https://techrt.com/android-launcher-statistics/
7. https://growth-onomics.com/mobile-app-retention-benchmarks-by-industry-2025/
8. https://www.pushwoosh.com/blog/increase-user-retention-rate/
9. https://www.scalebay.io/blog/app-retention-analysis-country-channel
10. https://www.reddit.com/r/ycombinator/comments/1f13tnn/what_are_the_general_industry_benchmark_retention/
11. https://business.mistplay.com/resources/mobile-app-user-retention-metrics
12. https://andrewchen.com/new-data-shows-why-losing-80-of-your-mobile-users-is-normal-and-that-the-best-apps-do-much-better/

---

*Research complete. Wave 2 research backlog: 5/5 done.*
