# Cortex Pulse Agent — External Automation Runbook

**Status:** Active build path  
**Automation Host:** External (Make.com / n8n / Zapier)  
**Spec:** [cortex-pulse-agent.md](./cortex-pulse-agent.md)  
**Owner:** Michael Ujuku Morim  
**Date:** 2026-09-16

---

## Goal of this runbook

Get the first working version of Cortex Pulse Agent live using an external automation platform.  
No code in the repo is required for the core loop. Everything lives in the automation tool + secrets.

---

## Recommended Tool Order

1. **Make.com** (easiest visual interface + good YouTube + social modules)  
2. **n8n** (self-hosted or cloud, more powerful, free options)  
3. **Zapier** (simplest but more limited free tier)

We will design the flow so it works on any of the three.

---

## High-Level Flow (v1)

```
YouTube (new video uploaded)
        ↓
Trigger: New video detected on @MikecomplexAI-i2e
        ↓
Extract: Title + Description + Video URL + Thumbnail
        ↓
Generate short platform-native captions (light adaptation only)
        ↓
Post to:
  • X
  • Telegram
  • LinkedIn
  • Bluesky
  • TikTok (if module available)
        ↓
Log activity (timestamp + platforms + post links)
```

---

## Required Accounts & Credentials

You (or I) will need access to these. Store them only inside the automation tool — never in the GitHub repo.

| Platform     | What is needed                          | Notes |
|--------------|-----------------------------------------|-------|
| YouTube      | Channel ID or RSS feed / API key        | Public channel is enough for monitoring |
| X (Twitter)  | API keys or connected account           | Preferred first platform |
| Telegram     | Bot token + Channel/Chat ID             | Very reliable |
| LinkedIn     | Company or personal page connection     | |
| Bluesky      | App password / session                  | |
| TikTok       | Business account + API (harder)         | Can be phase 2 |
| Logging      | Google Sheet or Notion database         | Simple activity log |

---

## Step-by-Step Build Order

### Phase 1 — Monitoring (do this first)
1. Create a new scenario / workflow called **Cortex Pulse – YouTube Monitor**
2. Trigger: “New video uploaded” on channel `@MikecomplexAI-i2e`
3. Test it with the latest video and confirm title + URL are captured

### Phase 2 — First Distribution (start with one platform)
Recommended order for speed:
1. Telegram (easiest and most reliable)
2. X
3. LinkedIn
4. Bluesky
5. TikTok later

### Phase 3 — Activity Log
- Create a simple Google Sheet or Notion database with columns:  
  `Date | Video Title | Video URL | Platforms Posted | Post Links | Notes`
- Append a row every time the agent runs

### Phase 4 — Full multi-platform + metrics
Only after Phase 1–3 are stable.

---

## Brand Rules (must be followed in every post)

- Public name: **Cortex Intelligence Nexus** only
- Never use “Mike Complex AI” as company name in public posts
- Keep the language practical, industrial, sovereign, Ogoja-rooted
- Always include the YouTube video link
- Prefer short, clear captions over long marketing text

---

## Current Decision Needed From You

To move forward without guessing, I need one answer:

**Which external tool do you already have (or prefer to use first)?**

Reply with one of:
- Make
- n8n
- Zapier
- None yet (I will guide you to open the easiest one)

Once you answer, I will give you the exact modules / steps for that tool and we continue building the first working scenario.

---

**Authority:** Michael Ujuku Morim  
**Next update after your tool choice**
