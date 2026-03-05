# User Feedback Loops & In-App Feedback Collection
## Wave 2 Research Brief — Oracle
**Date:** 2026-03-04

---

## Executive Summary

In-app feedback collection is critical for utility apps where user experience directly impacts retention. Mobile app surveys achieve **36.14% average response rate** (vs 26.48% for web), making them highly viable for Home Screen Organizer.

---

## 1. Best Practices for In-App Feedback

### Timing & Triggers
- **Post-action triggers:** After folder organization completes, after first app launch, after widget interaction
- **Exit-intent detection:** When user shows signs of churning or abandoning a feature
- **Milestone moments:** After X organization actions, after 7-day streak, after first custom folder created

### Survey Length
- Keep surveys to **1-3 questions maximum**
- Use micro-surveys (single-question) for highest completion
- In-app surveys should take <15 seconds to complete

### UI Patterns
- **Bottom sheet modals** — non-intrusive, easy to dismiss
- **Inline micro-surveys** — embedded within flows
- **Gesture-triggered** — long-press or shake to trigger feedback
- **Opt-in first** — don't interrupt; ask permission first

---

## 2. Survey Type Comparison: NPS vs Custom

| Metric | Response Rate | Use Case | Best For |
|--------|---------------|----------|----------|
| **NPS** | 15-30% | Loyalty measurement | Quarterly health checks |
| **CSAT** | 30-40% | Transaction-specific | After organization actions |
| **CES** (Customer Effort Score) | 25-35% | Usability | After first-time setup |

**Recommendation:** For utility apps, **CSAT outperforms NPS** in mobile contexts. Use transaction-specific CSAT after key actions rather than generic NPS.

---

## 3. TestFlight & Beta Feedback Integration

### TestFlight Built-in Feedback
- Testers can submit feedback **directly from within the app** via screenshot + text
- Crash reports auto-attach with feedback
- Access via App Store Connect → TestFlight → Feedback section
- **Limitation:** Only available during beta, not in production

### Product Hunt Feedback
- Launch on PH → Collect comments/feedback in PH thread
- Use PH as **feedback funnel** — direct users to in-app feedback after launch
- Monitor PH comments for feature requests

### Recommended Workflow
1. **Beta:** Use TestFlight built-in + custom in-app survey
2. **Launch:** Use PH launch post to gather initial user sentiment
3. **Production:** In-app CSAT + periodic NPS (quarterly)

---

## 4. Implementation Recommendations

### For Home Screen Organizer

**Phase 1 (MVP):**
- Post-first-launch CSAT (1 question: "How easy was it to organize your home screen?")
- In-app "Feedback" button in settings → opens email/feedback form

**Phase 2:**
- Triggered micro-surveys after: first folder created, widget added, after 7-day streak
- Rate-in-app prompt (Apple guidelines compliant) after positive sentiment

**Phase 3:**
- Quarterly NPS with follow-up "why" question for detractors
- Integration with support desk (Intercom, Zendesk) for high-priority feedback

### Tools to Evaluate
- **Zonka Feedback** — iOS SDK, segmentation, NPS/CSAT/CES
- **Refiner** — targeting, A/B testing surveys
- **Mixpanel** — event-triggered feedback within analytics
- **Custom** — build own bottom-sheet for full control

---

## 5. Key Sources

1. Refiner.io — "In-app Survey Response Rates: Benchmarks" (Nov 2025)
2. SurveyMonkey — "NPS Survey Best Practices" (Dec 2025)
3. Apple Developer — "TestFlight Feedback" documentation
4. Zonka Feedback — "In-App Feedback Tools 2026"
5. Alchemer — "How to Collect More In-App Feedback"

---

## 6. Risks & Considerations

- **Survey fatigue:** Limit to max 1 survey per user per week
- **Apple App Store guidelines:** Rate prompts must follow strict rules (only after significant engagement, no repeat prompts)
- **Privacy:** Clearly communicate how feedback is used; don't collect PII without consent

---

**Next Steps:**
- Designer: Design micro-survey UI patterns (bottom sheet, inline)
- Artisan: Evaluate Zonka Feedback SDK vs custom implementation
- Define feedback-to-roadmap process (weekly review of feedback themes)
