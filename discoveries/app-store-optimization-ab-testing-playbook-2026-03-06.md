# App Store Optimization A/B Testing Playbook
**Home Screen Organizer - Post-Launch Optimization**

**Research Date:** 2026-03-06  
**Author:** Oracle  
**Status:** Ready for implementation

---

## Executive Summary

Apple's Product Page Optimization (PPO) allows testing **3 visual elements**: app icon, screenshots, and app preview videos. Tests run up to 90 days with up to 3 treatments. Key insight: **icons require a new app build**, but screenshots and videos can be tested independently.

---

## Testable Elements

### 1. App Icon ⭐ HIGH IMPACT
**What you can test:** Colors, styles, symbols, minimal vs detailed designs

**Requirements:**
- All icon variants must be included in app binary
- Built with Xcode 13 or later
- Requires new app version submission for icon tests

**Test scenarios:**
- Color variations (e.g., blue vs purple vs green)
- Symbol clarity (folder icon vs grid icon vs abstract)
- Style (flat vs 3D/glass vs minimal)

**Timeline:** 2-4 weeks for build + approval + test

---

### 2. Screenshots ⭐⭐ HIGHEST IMPACT
**What you can test:** Order, messaging, style, features highlighted

**Requirements:**
- No app update required
- Can test independently of icon/video
- Up to 10 screenshots per device size

**Test scenarios:**
- First screenshot: Feature showcase vs transformation (before/after)
- Messaging: "Organize in 1 tap" vs "AI-powered sorting"
- Style: Real UI mockups vs stylized illustrations
- Order: Most-used features first vs aha moment first

**Timeline:** Can start immediately after launch

---

### 3. App Preview Videos ⭐ MEDIUM IMPACT
**What you can test:** Length, pacing, narrative, features shown

**Requirements:**
- 15-30 seconds max
- Under 500 MB
- Must match real UI
- No app update required

**Test scenarios:**
- 15s fast-paced vs 30s detailed walkthrough
- Voiceover vs text-only vs silent
- Single feature deep-dive vs overview

**Timeline:** Can start immediately after launch

---

## What You CANNOT Test with PPO

- App name/title
- Subtitle
- Description
- Keywords
- Promotional text
- What's New

**These require standard metadata updates** and cannot be A/B tested natively in App Store Connect.

---

## Statistical Significance Guidelines

### Apple's Confidence Threshold
- **90% confidence** required before declaring a winner
- Apple provides real-time confidence indicators in App Analytics
- Tests can run up to 90 days

### Sample Size Requirements

| Daily Impressions | Estimated Days to 90% Confidence |
|-------------------|-----------------------------------|
| 1,000 | 60-90 days |
| 5,000 | 21-45 days |
| 10,000 | 14-30 days |
| 50,000+ | 7-14 days |

### Traffic Allocation

**Recommended split:**
- **Small apps (<5K daily impressions):** 50% to test (25% each treatment)
- **Medium apps (5-20K):** 30% to test (10% each treatment)
- **Large apps (20K+):** 20% to test

**Rule:** Higher traffic allocation = faster results, but more users see potentially suboptimal variants.

---

## Prioritized Experiments for Home Screen Organizer

### Priority 1: Screenshot Ordering (Week 1-4)
**Hypothesis:** Showing the "aha moment" transformation first will increase CVR by 15%+

**Test Setup:**
- **Control:** Current screenshot order (feature showcase)
- **Treatment A:** Before/after transformation as first screenshot
- **Treatment B:** "1-tap organize" value prop as first screenshot
- **Traffic:** 40% (20% each treatment)
- **Duration:** 30 days

**Success Metric:** Conversion rate improvement ≥10% with 90% confidence

---

### Priority 2: Screenshot Messaging (Week 4-8)
**Hypothesis:** Benefit-focused captions outperform feature-focused captions

**Test Setup:**
- **Control:** "Sort apps automatically"
- **Treatment A:** "Find any app in seconds"
- **Treatment B:** "Save 2 hours per week"
- **Traffic:** 30% (10% each treatment)
- **Duration:** 30 days

**Success Metric:** Conversion rate improvement ≥8% with 90% confidence

---

### Priority 3: App Icon Color (Month 2-3)
**Hypothesis:** A distinct color will improve browse conversion by 10%+

**Test Setup:**
- **Control:** Current icon color
- **Treatment A:** Alternative color 1
- **Treatment B:** Alternative color 2
- **Traffic:** 40% (20% each treatment)
- **Duration:** 45 days
- **Note:** Requires new app build with alternate icons in binary

**Success Metric:** Conversion rate improvement ≥10% with 90% confidence

---

## Tracking & Tools

### Native (Free)
- **App Store Connect App Analytics:** Built-in PPO tracking
- Shows impressions, conversion rate, confidence level
- Compare treatments against baseline

### Third-Party (Paid)
- **AppTweak:** Competitor PPO tracking, timeline view
- **MobileAction:** PPO intelligence, CPP performance tracking
- **Appfigures:** Test duration estimates, significance calculator

### Integration with Supabase
Track PPO performance alongside other metrics:
```sql
-- Example: Track PPO test performance by date
INSERT INTO analytics_events (event_type, properties, created_at)
VALUES ('ppo_test_view', '{"test_id": "...", "treatment": "A"}', NOW());
```

---

## Best Practices

### Do's ✅
1. **Test ONE element at a time** when possible (isolates impact)
2. **Wait for 90% confidence** before applying treatment
3. **Run tests for minimum 14 days** to account for day-of-week variance
4. **Document hypotheses** before starting tests
5. **Archive losing variants** for future reference

### Don'ts ❌
1. **Don't change test mid-run** (invalidates results)
2. **Don't test more than 3 treatments** (slows significance)
3. **Don't apply treatments prematurely** (wait for confidence)
4. **Don't test text metadata** (not supported by PPO)
5. **Don't ignore iOS 15+ limitation** (older iOS users see original)

---

## Launch Timeline

| Week | Activity |
|------|----------|
| 1-2 | Monitor baseline conversion rate |
| 2-3 | Design screenshot variants |
| 3 | Submit PPO test #1 (screenshot order) |
| 3-6 | Run test, monitor daily |
| 6 | Apply winning treatment or extend test |
| 7-8 | Design messaging variants |
| 8 | Submit PPO test #2 (messaging) |
| 8-12 | Run test, apply winner |
| Month 3 | Prepare icon variants in next app build |

---

## Sources

1. Apple Developer Documentation - Product Page Optimization (developer.apple.com)
2. MobileAction - App Store Product Page Optimization Guide 2026
3. YellowHEAD - Product Page Optimization and iOS A/B Testing
4. AppTweak - PPO Tips & Best Practices
5. Appfigures - How To Run A/B Tests in App Store Connect
6. Appbot - A/B Testing App Icons in App Store Connect

---

_Deliverable for Task j9722ajad1f2g8f9623ed74qsd82cz84_
_Oracle Research - 2026-03-06_