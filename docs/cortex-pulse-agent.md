# Cortex Pulse Agent

**Status:** Specification locked — First build slice  
**Owner:** Michael Ujuku Morim (absolute authority)  
**Repo:** Cortex-Nexus-Sovereign-Industrial-AI/cortex-platform-core  
**Related live surfaces:**  
- Admin: https://cortex-nexus-sovereign-industrial-ai.github.io/cortex-platform-core/admin/dashboard.html  
- Customer Portal: https://cortex-nexus-sovereign-industrial-ai.github.io/cortex-platform-core/customer/portal.html  
- Primary platform: https://cortex-platforms.netlify.app  
- YouTube: @MikecomplexAI-i2e

---

## Purpose

Cortex Pulse Agent is the automated content distribution and activity tracking system for Cortex Intelligence Nexus.

It turns every new YouTube upload into a controlled, multi-platform distribution event without manual share links.

---

## Core Responsibilities (v1 Scope)

1. **Monitor**  
   - Watch YouTube channel `@MikecomplexAI-i2e` for new video uploads.

2. **Distribute**  
   - Auto-generate and post platform-native versions of the new content to:  
     - TikTok  
     - LinkedIn  
     - Telegram  
     - X (Twitter)  
     - Bluesky  
   - Use the founder’s natural voice and terminology (industrial AI, sovereign systems, Ogoja, practical execution language).

3. **Track**  
   - Capture basic metrics after posting: views, likes/reactions, comments, shares where available.  
   - Store a simple activity log (timestamp + platform + post URL + basic metrics).

4. **Brand Guardrails**  
   - Public brand name remains **Cortex Intelligence Nexus** only.  
   - Internal runner name (Mike Complex AI) is never used as public company identity.  
   - All posts must align with verified Google Business Profile and IDENTITY.md rules.

---

## Explicit Non-Goals (v1)

- No full video re-encoding or heavy media processing in the first version.  
- No complex AI rewriting of titles/descriptions beyond light platform adaptation.  
- No paid ads automation.  
- No employee/HR data handling.  
- No automatic replies or comment engagement in v1.

---

## Success Criteria for First Working Version

- Detects a new YouTube upload within a reasonable window (target < 30–60 minutes).  
- Successfully posts a clean, on-brand message + link to at least 3 of the 5 target platforms.  
- Creates a readable activity log entry for each distribution event.  
- Zero manual share-link steps required after the initial setup.

---

## Technical Notes (Implementation Direction)

- Preferred lightweight stack: GitHub Actions + simple scripts, or Netlify Functions + scheduled jobs, or Make.com / n8n / Zapier as bridge if credentials are easier.  
- Credentials and API keys must live only in environment variables / secrets — never committed.  
- Activity log can start as a simple Markdown or JSON file in the repo or a private Notion/Google Sheet, then move to structured storage later.

---

## Next Build Steps (in order)

1. ✅ This specification document.  
2. Decide primary automation host (GitHub Actions vs Netlify Functions vs external tool).  
3. Create the monitoring trigger for new YouTube videos.  
4. Create the first platform poster (start with one platform — recommended: X or Telegram for speed).  
5. Expand to remaining platforms.  
6. Add basic metrics capture + activity log.

---

**Authority:** Michael Ujuku Morim  
**Last updated:** 2026-09-16
