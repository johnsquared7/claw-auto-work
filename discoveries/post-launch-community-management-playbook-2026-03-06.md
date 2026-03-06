# Post-Launch Community Management Playbook

**Research Date:** March 6, 2026  
**App:** Home Screen Organizer  
**Target:** Early adopter community management for first 90 days post-launch

---

## Executive Summary

Post-launch community management is about **turning early adopters into ambassadors**. The first 90 days are critical: users who feel heard become vocal advocates. This playbook covers community setup, engagement cadence, champion identification, FAQ management, and escalation workflows.

**Key Insight:** Direct outreach + community engagement beats advertising for early growth. Founders who identify 50 specific individuals and engage personally see 10x better conversion than broad campaigns.

---

## 1. Community Platform Decision

### Discord vs Slack vs Discourse

| Platform | Best For | Pros | Cons |
|----------|----------|------|------|
| **Discord** | Consumer apps, gaming, younger demographics | Free, unlimited history, voice/video, 150M+ MAU | Gaming UI may feel casual |
| **Slack** | B2B, professional audiences | Familiar to business users, integrations | Paid plans for history, limited file size |
| **Discourse** | Long-form discussions, documentation | SEO benefits, structured threads | Lower engagement, requires hosting |

**Recommendation for Home Screen Organizer:** **Discord**
- Free with unlimited message history
- Strong moderation tools (AutoMod, Mod Academy)
- Growing integrations (GitHub, Twitter, Zapier)
- Appeals to productivity/tech enthusiasts

---

## 2. Discord Server Setup (Week 0)

### Server Structure

```
📂 Welcome
  #welcome - Auto-welcome message, rules
  #announcements - Product updates, changelog
  #introductions - New member intros

📂 General
  #general - Off-topic chat
  #feedback - Feature requests, bug reports
  #show-your-setup - Home screen screenshots

📂 Support
  #help - Quick questions
  #known-issues - Pinned current bugs
  #faq - Auto-populated from FAQ doc

📂 VIP (Early Adopters / Beta Testers)
  #early-access - Beta builds discussion
  #feature-voting - Roadmap input
  #founders-chat - Direct line to team

📂 Voice
  🔊 Community Office Hours - Weekly drop-in
  🔊 Co-working - Optional background chat
```

### Roles & Permissions

| Role | Description | Permissions |
|------|-------------|-------------|
| @Admin | Full server control | All permissions |
| @Moderator | Community management | Kick, ban, manage messages |
| @Staff | Team members | Announce, pin, manage channels |
| @EarlyAdopter | Beta testers, first 100 users | VIP channels, special badge |
| @Champion | Identified ambassadors | Same as EarlyAdopter + direct founder DM |
| @Member | Verified users | General channels |

### First-Day Setup Checklist
- [ ] Create server with Early Access template
- [ ] Set up AutoMod rules (spam, links, mentions)
- [ ] Write welcome message with onboarding flow
- [ ] Create `#rules` with clear community guidelines
- [ ] Enable Server Insights (Community feature)
- [ ] Set up bot for auto-welcome (MEE6, Carl-bot)
- [ ] Create `#get-roles` reaction role system

---

## 3. Engagement Cadence (First 90 Days)

### Week 1-2: Foundation
- **Daily:** Check all channels, respond within 4 hours
- **Daily:** Post one engaging question or tip
- **Daily:** Welcome every new member personally
- **Weekly:** "What we shipped this week" announcement

### Week 3-4: Activation
- **Daily:** Continue rapid response
- **Bi-weekly:** Office hours voice chat (30 min)
- **Weekly:** Feature spotlight post
- **Weekly:** Share user-submitted home screens (with permission)

### Month 2: Champion Identification
- **Daily:** Monitor for high-engagement users
- **Weekly:** DM top contributors personally
- **Bi-weekly:** Champion-only feedback session
- **Monthly:** "Community Spotlight" post

### Month 3: Ambassador Program Launch
- **Weekly:** Champion onboarding (3-5 new/month)
- **Monthly:** Ambassador newsletter with insider info
- **Monthly:** Roadmap preview for champions
- **Ongoing:** Champion-led events (show-and-tell, tutorials)

---

## 4. User Champion Identification

### What Makes a Champion

**Behavioral Signals:**
- Responds to other users' questions unprompted
- Submits detailed, thoughtful feedback
- Shares home screen setups publicly
- High message frequency (5+ per week)
- Active in voice channels or events
- Mentions the app organically on other platforms

**Quantitative Signals:**
- Top 10% in message count
- 90%+ positive sentiment in messages
- Joined in first 30 days
- Uses app daily (if trackable)
- Refers other users

### Champion Identification Process

1. **Track:** Use Discord Insights or bot to identify top contributors weekly
2. **Review:** Manually review message quality (not just quantity)
3. **Qualify:** Check for genuine enthusiasm vs. help-seeking behavior
4. **Reach Out:** Personal DM: "Hey [name], noticed you've been super active and helpful. Would love to chat about making you an official champion."

### Champion Onboarding

**Perks to Offer:**
- `@Champion` role with unique color/badge
- Private channel with founders
- Early access to new features
- Monthly 1:1 with product team
- Swag (if budget allows)
- Public recognition in announcements
- Input on roadmap priorities

**Expectations:**
- Respond to 3+ community questions/week
- Provide feedback on beta features
- Represent the brand positively
- Flag issues early
- (Optional) Create content (tutorials, screenshots)

---

## 5. FAQ Management

### FAQ Source Pipeline

1. **Discord Questions** → Track via bot or manual review
2. **App Store Reviews** → Pull via Forge automation (already set up)
3. **Reddit Mentions** → Manual search or Mention tools
4. **Support Emails** → Tag and categorize
5. **In-App Feedback** → Supabase analytics

### FAQ Categorization

| Category | Examples | Response Owner |
|----------|----------|----------------|
| Onboarding | "How do I..." | Auto-response + help doc link |
| Features | "Can it do..." | Product team decision |
| Pricing | "Is it free..." | Pre-written response |
| Technical | "It crashed..." | Escalate to support |
| Privacy | "Does it access..." | Pre-written response |

### FAQ Maintenance Process

- **Daily:** Review new questions in `#help`
- **Weekly:** Update FAQ document with new patterns
- **Weekly:** Add missing FAQ items to `#faq` channel
- **Monthly:** Review FAQ analytics (most viewed, still-asked)
- **Quarterly:** Full FAQ audit and refresh

### FAQ Response Templates

**Feature Request:**
> "Great idea! I've logged this for the team. Can you tell me more about how you'd use this? The more detail, the better we can prioritize."

**Bug Report:**
> "Thanks for reporting! Can you share: 1) iOS version, 2) Device model, 3) Steps to reproduce? I'll make sure the dev team sees this."

**Pricing Question:**
> "Good question! The core app is free with [X premium features]. We offer a 7-day free trial so you can test everything. Any specific features you're curious about?"

---

## 6. Escalation Workflows

### Triage Levels

| Level | Type | Response Time | Action |
|-------|------|---------------|--------|
| **P0** | App crash, data loss, security issue | < 1 hour | Immediate dev alert, status page update |
| **P1** | Major feature broken, widespread bug | < 4 hours | Dev investigation, workaround posted |
| **P2** | Minor bug, feature confusion | < 24 hours | Log for fix, help user |
| **P3** | Feature request, feedback | < 48 hours | Acknowledge, log to backlog |

### Escalation Channels

```
Discord #help → Community Manager triage
    ↓
P0: @dev-team Discord ping + Slack alert
P1: #known-issues post + dev ticket
P2: Linear ticket + weekly dev sync
P3: Notion backlog + monthly review
```

### Escalation Template (Internal)

```markdown
**Priority:** P[0-3]
**User:** [Discord handle]
**Issue:** [1-2 sentence description]
**Repro Steps:** [If applicable]
**Impact:** [Users affected / business impact]
**First Response:** [What was said to user]
**Owner:** [Who's handling]
```

---

## 7. Community Health Metrics

### Track Weekly

| Metric | Target | Tool |
|--------|--------|------|
| New members | Growth | Discord Insights |
| Activation rate (messaged day 1) | > 40% | Discord Insights |
| Weekly active members | > 20% of total | Discord Insights |
| Avg response time | < 4 hours | Manual |
| Champion-to-member ratio | 1:50 | Manual count |
| Sentiment (positive/neutral/negative) | > 80% positive | Manual review or bot |

### Track Monthly

| Metric | Target | Tool |
|--------|--------|------|
| Member retention (returned week 2) | > 30% | Discord Insights |
| User-generated content posts | 5+ | Manual |
| Feature requests submitted | Track volume | Notion |
| Bugs caught via community | Track volume | Linear |
| App Store reviews mentioned community | Track correlation | Manual |

---

## 8. Launch Day Community Checklist

**Before Launch:**
- [ ] Discord server live with all channels
- [ ] Welcome message and rules finalized
- [ ] At least 2 moderators available (team members)
- [ ] FAQ pre-populated with expected questions
- [ ] AutoMod rules configured
- [ ] `#announcements` ready for launch post
- [ ] Invite link ready for marketing channels

**Launch Day:**
- [ ] Post launch announcement in `#announcements`
- [ ] Monitor all channels continuously (12+ hours)
- [ ] Welcome every new member
- [ ] Respond to every question within 2 hours
- [ ] Flag any P0/P1 issues immediately
- [ ] Share in general channels periodically

**Launch Week:**
- [ ] Daily engagement posts (questions, tips)
- [ ] Identify first 5 champion candidates
- [ ] Post "Week 1 Retrospective" with fixes/shipping
- [ ] Review all feedback and categorize
- [ ] Update FAQ with new questions

---

## Sources

1. Discord Game Developer Playbook Part 2 - Early Access & Pre-Launch (discord.com/blog)
2. Common Room - Ultimate Guide to Discord Community Management
3. Medium - Turning Early Adopters into Ambassadors (Aleksandar Tisma)
4. Higher Logic - Building an Online Community Super Users Program
5. Reddit r/SaaS - Early Adopter Strategies
6. LoyaltySurf - SaaS Advocate Program Examples

---

## Summary

**Community success = fast response + genuine connection + champion empowerment.**

Start with Discord. Set up structure before launch. Engage daily. Identify champions by week 3. Scale through ambassadors by month 3. The community that feels heard becomes your best marketing channel.