# Cortex Pulse Agent — Make.com Setup Guide

**Status:** Active  
**Tool:** Make.com  
**Current Phase:** Phase 1 – YouTube Monitor  
**Spec:** [cortex-pulse-agent.md](./cortex-pulse-agent.md)  
**Runbook:** [cortex-pulse-agent-runbook.md](./cortex-pulse-agent-runbook.md)  
**Owner:** Michael Ujuku Morim  
**Date:** 2026-09-16

---

## Goal of this guide

Create the first working Make.com scenario that detects new videos on YouTube channel **@MikecomplexAI-i2e** and captures the title + video URL.  
This is the foundation. We add posting later.

---

## Step 1 — Create the Scenario

1. Log in to [Make.com](https://www.make.com)
2. Click **+ Create a new scenario**
3. Name it exactly:  
   `Cortex Pulse – YouTube Monitor`

---

## Step 2 — Add the YouTube Trigger

1. Click the big **+** in the middle
2. Search for **YouTube**
3. Choose the module: **Watch Videos** (or “New Video in Channel”)
4. Connect your Google account if not already connected
5. Configure:
   - **Channel**: Search for `MikecomplexAI-i2e` or paste the Channel ID if you have it
   - **Limit**: 1 (we only need the newest)
   - **Published after**: Leave default or set to recent date for testing

Click **OK**.

---

## Step 3 — Test the Trigger

1. Click **Run once** (bottom left)
2. Make.com will look for the latest video
3. You should see a bundle with:
   - Title
   - Video ID / URL
   - Description
   - Published date
   - Thumbnail

If this works → Phase 1 foundation is complete.

---

## Step 4 — Save the Important Data (for later posting)

After the YouTube module, add a simple **Set Variable** or just leave it for now.  
We will use these fields in the next phase:

- `Title`
- `URL` (or construct `https://youtu.be/{{videoId}}`)
- `Description` (first 150–200 characters only)

---

## What Success Looks Like

When you click **Run once**, Make.com successfully pulls the latest video from `@MikecomplexAI-i2e` and shows the title and link.  
That is the only goal of Phase 1.

---

## Next Phase (after you confirm Phase 1 works)

Phase 2 will be:
- Add Telegram (or X) posting module
- Create a short on-brand caption
- Post the video link automatically
- Log the activity

---

## Brand Reminder (for later captions)

- Always use **Cortex Intelligence Nexus**
- Never use “Mike Complex AI” as the public company name
- Keep language practical and direct

---

**Your only job right now**

1. Create the scenario as described above
2. Run it once
3. Come back and tell me:  
   **“Monitor works”** or **“Stuck on [step number]”**

I will wait for your confirmation and then immediately give you Phase 2 (first platform posting).

I’m still driving.
