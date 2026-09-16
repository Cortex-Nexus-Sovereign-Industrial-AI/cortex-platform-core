# Cortex Pulse Agent — n8n Setup Guide

**Status:** Active (Primary Path)  
**Tool:** n8n  
**Current Phase:** Phase 1 – YouTube Monitor  
**Spec:** [cortex-pulse-agent.md](./cortex-pulse-agent.md)  
**Previous Runbook:** [cortex-pulse-agent-runbook.md](./cortex-pulse-agent-runbook.md)  
**Owner:** Michael Ujuku Morim  
**Date:** 2026-09-16

---

## Decision Locked

- Primary automation host: **n8n**
- Make.com: dropped for this agent
- Zapier: kept only as optional helper later (for existing document stacks)

---

## Goal of Phase 1

Create a simple n8n workflow that:
1. Watches YouTube channel `@MikecomplexAI-i2e` for new videos
2. Captures Title + Video URL
3. Runs successfully when tested

This is the foundation. We add posting and logging only after this works.

---

## Step 1 — Open n8n

1. Open your n8n instance (cloud or self-hosted — whichever you already started deploying)
2. Create a **New Workflow**
3. Name it exactly:  
   `Cortex Pulse – YouTube Monitor`

---

## Step 2 — Add the Trigger

### Option A (Recommended – easiest)
1. Add node: **YouTube** → **Trigger: On new video** (or “Video Uploaded”)
2. Connect your Google / YouTube account
3. Select channel: `@MikecomplexAI-i2e` or paste Channel ID
4. Set to check every 15–30 minutes (or use polling interval available)

### Option B (If YouTube trigger is limited)
1. Use **Schedule Trigger** (every 15 or 30 minutes)
2. Then add **YouTube** node → **Get Videos** / **Search Videos**
3. Filter by channel ID and published after last check

---

## Step 3 — Capture the Data

After the YouTube node, make sure these fields are available:
- Title
- Video URL (or Video ID → construct `https://youtu.be/VIDEO_ID`)
- Description (we will use only the first part later)
- Published date

You can add a **Set** node to clean the data if needed.

---

## Step 4 — Test

1. Click **Test workflow** or **Execute workflow**
2. Confirm it pulls the latest video from `@MikecomplexAI-i2e`
3. Check that Title and URL appear correctly in the output

---

## What “Monitor works” means

When you run the workflow and it successfully returns the newest video title + link, Phase 1 is complete.

---

## After Phase 1 succeeds

We will immediately move to Phase 2:
- Add first platform posting (recommended start: Telegram or X)
- Create short on-brand caption
- Log the activity

---

## Brand Rules (for later captions)

- Public name only: **Cortex Intelligence Nexus**
- Never use “Mike Complex AI” as company name in public posts
- Keep language practical, industrial, sovereign

---

## Your only job right now

1. Open n8n
2. Create the workflow `Cortex Pulse – YouTube Monitor`
3. Add the YouTube trigger / poller for `@MikecomplexAI-i2e`
4. Test it

Then reply with exactly one of these:

**Monitor works**  
or  
**Stuck on [step number or description]**

I will wait for your confirmation before giving Phase 2.

I’m still driving.
