# Cortex Intelligence Nexus - Deployment Guide
# Canonical Deployment for cortex-platform-core

**Repo:** `Cortex-Nexus-Sovereign-Industrial-AI/cortex-platform-core`  
**Status:** PUBLIC, GitHub Pages ENABLED (has_pages: true)  
**Canonical URL:** https://cortex-nexus-sovereign-industrial-ai.github.io/cortex-platform-core/  
**Secondary:** https://cortex-platforms.netlify.app/  
**CEO:** Michael Morim - 27 Mission Rd, Ogoja | Hardware: No.7 Calabar St, Ogoja 550101

## TODAY'S PRIORITY EXECUTION SEQUENCE

### 1. Confirm GitHub Pages (DONE)
- Settings → Pages → Source: Deploy from main branch / root
- Verify has_pages: true
- Visibility: PUBLIC required for Pages

### 2. Push 4 Pending Files (ATOMIC COMMIT)

```
git add admin/dashboard.html
git add customer/portal.html
git add docs/deployment-guide.md
git add docs/navigation-flows.md
git commit -m "feat: TODAY'S PRIORITY - admin dashboard, customer success portal, deployment guide, navigation flows - atomic push for Pages verification"
git push origin main
```

### 3. Stack Verification Post-Push

- File paths must be case-sensitive exactly:
  - `/admin/dashboard.html`
  - `/customer/portal.html`
  - `/docs/deployment-guide.md`
  - `/docs/navigation-flows.md`

- Wait 60-120s for GitHub Pages build

### 4. Live URL Verification

Check these URLs return 200:

- https://cortex-nexus-sovereign-industrial-ai.github.io/cortex-platform-core/
- https://cortex-nexus-sovereign-industrial-ai.github.io/cortex-platform-core/admin/dashboard.html
- https://cortex-nexus-sovereign-industrial-ai.github.io/cortex-platform-core/customer/portal.html

If 404 → Check Pages build logs in Actions tab

## Infrastructure

- **Hosting:** GitHub Pages (primary for this repo), Netlify (cortex-platforms.netlify.app secondary)
- **DNS/Security:** Cloudflare
- **Automation:** Zapier, Make.com, n8n, Botpress, Zabia OpenAI Analyze Text
- **Dev Stack:** Python, JavaScript, HTML, CSS, YAML, shell on Android Termux/Pydroid 3, Target i7, Samsung/Apple, Brave/Chrome/Samsung Internet
- **Finance Rails:** Moniepoint, Opay, MoreMins, SocioSMS, CSCS Nigerian capital market
- **Creator Accounts:** YouTube @MikecomplexAI-i2e, Telegram, LinkedIn, Substack, Pinterest, X, Bluesky, TikTok, Quora Spaces, Notion, Canva

## Blocker Flag Protocol

If any file fails to deploy, immediately flag:
- File name
- Build error from GitHub Actions → Pages build and deployment
- Check repo visibility still PUBLIC
- Check Pages source still main / root

## Monetization → Knowledge → Support → Expansion → Compliance

This deployment locks LAYER 2 (Knowledge) to live URL, enabling LAYER 1 (Monetization) payment links and LAYER 3 (Support) HRbot WhatsApp/YouTube integration.