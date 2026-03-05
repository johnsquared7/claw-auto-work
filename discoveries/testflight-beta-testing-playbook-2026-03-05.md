# TestFlight Beta Testing Playbook

**For:** Home Screen Organizer iOS App Launch
**Research Date:** 2026-03-05
**Source:** Oracle Research

---

## TL;DR Quick Reference

| Metric | Limit |
|--------|-------|
| Internal Testers | 100 (instant, no review) |
| External Testers | 10,000 (requires Beta App Review) |
| Build Expiration | 90 days |
| Beta Review Time | 24-48 hours |
| Cost | Free (included with Apple Developer Program) |

---

## Setup Checklist

### Prerequisites
- [ ] Apple Developer Program membership active
- [ ] App record created in App Store Connect
- [ ] Bundle identifier matches App Store Connect
- [ ] Build passes basic validation

### Upload Options
1. **Xcode** (recommended): Product → Archive → Distribute App → App Store Connect
2. **Xcode Cloud**: CI/CD auto-upload on branch push
3. **Fastlane**: `pilot` command for scripted uploads
4. **Transporter app**: Manual upload

### Processing Time
- 5-30 minutes typical
- Check email for processing errors
- Common issues: invalid provisioning profile, missing icons

---

## Testing Strategy: Phased Rollout

### Phase 1: Internal Testing (Day 1-3)
- **Who:** Team members, stakeholders (up to 100)
- **Speed:** Instant access after processing
- **Focus:** Crash testing, critical flows, obvious bugs
- **No Beta App Review required**

### Phase 2: Closed Beta (Week 1-2)
- **Who:** 50-200 trusted external testers
- **Requires:** Beta App Review (24-48 hours)
- **Method:** Email invites or private public link
- **Focus:** UX feedback, edge cases, device diversity

### Phase 3: Open Beta (Week 2-4)
- **Who:** 500-2,000 public testers
- **Method:** Public link with cap
- **Focus:** Performance validation, scale testing, final polish

---

## Beta App Review

### What Gets Checked
- App doesn't crash on launch
- Basic functionality works
- No guideline violations
- Appropriate metadata
- No malware

### What's OK (Beta Tolerance)
- Minor UI bugs
- Incomplete features
- Placeholder content (within reason)
- Performance not fully optimized

### Review Tips
- First build triggers review; subsequent builds with same testers often skip
- Beta rejection doesn't affect App Store standing
- Fix issues and resubmit new build

---

## Required Metadata

For external testing, provide:

| Field | Content |
|-------|---------|
| Beta App Description | What you're testing, what to focus on |
| Feedback Email | Where to send bug reports |
| What to Test | Specific features/flows |
| Demo Account | If app requires login (same as App Store review) |

---

## Tester Management

### Internal Testers
- Must be App Store Connect team members
- Roles: App Manager or Developer
- Invite via Users and Access → add to Internal Testing group
- Instant email invite

### External Testers
**Option A: Email Invites**
- Add manually or import CSV
- Each gets personalized invite
- Good for controlled betas

**Option B: Public Link**
- Anyone with link can join
- Set cap (e.g., 500 testers)
- Can disable anytime
- Good for social media promotion

### Tester Segmentation Strategy
Create specialized groups:
- **Core functionality testers** - critical user journeys
- **Edge case hunters** - tech-savvy, explore boundaries
- **UX/UI specialists** - design-focused feedback
- **Device diversity team** - various models/OS versions

---

## Feedback Collection

### Built-in TestFlight Tools
- Screenshot annotation
- Automatic crash reports
- Direct email via TestFlight app

### Recommended Additions
1. **In-app feedback button** - opens form/email without leaving app
2. **Discord/Slack channel** - real-time tester community
3. **Structured surveys** - Typeform/Google Forms with specific questions

### Feedback Management
- Categorize: Critical / Major / Minor / Enhancement
- Assign severity for prioritization
- Integrate with issue tracking (Linear, GitHub)
- Designate team member for feedback triage

---

## Common Issues & Fixes

| Issue | Solution |
|-------|----------|
| Build stuck processing | Check email for errors, verify archive settings, reupload |
| Testers not receiving invites | Check spam, use public link backup, resend invite |
| "Unable to Install" error | Check deployment target matches device/OS |
| Beta review rejected | Fix specific issue, submit new build |
| Build expired | Upload new build before 90-day expiration |

---

## Transition to App Store Launch

### Pre-Launch Checklist
- [ ] All critical bugs resolved
- [ ] Analytics verified (Firebase/Amplitude)
- [ ] In-app purchases tested in sandbox
- [ ] App Store metadata ready
- [ ] Screenshots and preview video prepared
- [ ] Demo account configured for review

### Build Expiration Warning
- Testers see warning before expiration
- Plan new build upload at 60-day mark if still testing
- Communicate expectations to testers

---

## Key Takeaways

1. **Always test internally first** - instant, catches obvious bugs before Beta Review
2. **Use phased rollouts** - contain damage from bad builds
3. **Segment testers** - targeted feedback over generic comments
4. **Add in-app feedback** - TestFlight built-in tools are limited
5. **Plan for 90-day expiration** - set calendar reminder at 60 days
6. **Beta rejections don't hurt** - fix and resubmit, no penalty

---

## Sources

1. iOS Submission Guide - TestFlight Complete Guide (Dec 2025)
2. MetaCTO - Mastering TestFlight (July 2025)
3. Apple Developer Documentation - TestFlight Overview
4. Kodeco - iOS App Distribution Best Practices
5. Reddit r/iOSProgramming - Launch Strategy Discussion

---

*Compiled by Oracle Research Agent*
*Task ID: j97cp9wv70rt5jkfj5q5mh6jg582a5jm*