# Deployment Guide: Cortex Intelligence Nexus Platform

## Overview

This guide covers deployment of the Cortex Platform Core via GitHub Pages, CI/CD configuration, monitoring, and rollback procedures for the CINIS Enterprise Governance Framework.

**Canonical Deployment:** `https://cortex-nexus-sovereign-industrial-ai.github.io/cortex-platform-core/`

---

## 1. GitHub Pages Setup

### Enable GitHub Pages

1. Navigate to repository **Settings** → **Pages**
2. Under "Source," select `main` branch
3. Folder: `/root` (default)
4. Save settings
5. Deployment will trigger automatically on push to `main`

### Custom Domain (cortexnexus.com)

1. In **Settings** → **Pages**, add custom domain: `cortexnexus.com`
2. Verify DNS records with your registrar:
   ```
   CNAME cortexnexus.com → cortex-nexus-sovereign-industrial-ai.github.io
   ```
3. Enable HTTPS enforcement once DNS propagates (4-24 hours)

---

## 2. File Structure

```
cortex-platform-core/
├── index.html                    # Main landing page
├── admin-dashboard.html          # Operator metrics portal
├── customer-success-portal.html  # Customer onboarding
├── projects.html                 # Project showcase
├── research.html                 # Research hub
├── support.html                  # Support/contact
├── media.html                    # Media assets
├── documentation.html            # Documentation index
├── styles.css                    # Global styles
├── DEPLOYMENT_GUIDE.md          # This file
├── NAVIGATION_FLOWS.md          # UX journey documentation
├── MISSION_STATEMENT.md         # Platform mission
├── ORGANIZATION.md              # Org structure
├── TECHNOLOGY_STACK.md          # Tech decisions
├── GOVERNANCE.md                # Governance framework
├── ARCHITECTURE_DECISION_RECORDS.md  # ADRs
└── .github/workflows/           # CI/CD automation
    └── deploy.yml               # GitHub Pages build/deploy
```

---

## 3. CI/CD Pipeline

### GitHub Actions Workflow

Create `.github/workflows/deploy.yml`:

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches:
      - main
  pull_request:
    branches:
      - main

jobs:
  validate:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      
      - name: Validate HTML
        run: |
          for file in *.html; do
            echo "Validating $file..."
            # Add HTML5 validator or link checker here
          done
      
      - name: Check CSS syntax
        run: |
          npm install -g stylelint
          stylelint "*.css" || true

  deploy:
    needs: validate
    if: github.ref == 'refs/heads/main' && github.event_name == 'push'
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      
      - name: Deploy to GitHub Pages
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./
          cname: cortexnexus.com
```

### Deployment Trigger

- **Automatic:** Every push to `main`
- **Manual:** Via GitHub Actions UI
- **Approval:** Pull request reviews before merge

---

## 4. Monitoring & Health Checks

### Uptime Monitoring

Use Uptimerobot or similar to monitor:
- `https://cortex-nexus-sovereign-industrial-ai.github.io/cortex-platform-core/`
- `https://cortexnexus.com/`

Alert on:
- HTTP status != 200
- Response time > 3s
- Certificate expiry within 7 days

### Performance Metrics

Monitor via Google Analytics or Plausible:
- Page load time (target: <2s)
- Bounce rate (target: <20%)
- Traffic by region (Ogoja-focused)
- Device breakdown

### Error Tracking

- Enable Google Search Console for indexing issues
- Monitor 404s and redirects via server logs
- Alert on SSL/TLS certificate errors

---

## 5. Deployment Checklist

Before each release:

- [ ] All HTML files validated (W3C HTML5)
- [ ] CSS passes stylelint checks
- [ ] Links tested (internal + external)
- [ ] Images optimized (<100KB each)
- [ ] Mobile responsiveness verified
- [ ] Browser compatibility tested (Chrome, Firefox, Safari, Edge)
- [ ] Accessibility (WCAG 2.1 AA) confirmed
- [ ] SEO meta tags present (title, description, keywords)
- [ ] Open Graph tags for social sharing
- [ ] Security headers set (CSP, X-Frame-Options, etc.)
- [ ] Performance audit run (target: Lighthouse >90)
- [ ] Content reviewed by Michael & team
- [ ] PR reviewed by at least one maintainer
- [ ] Merge to `main` and verify deployment

---

## 6. Rollback Procedure

If deployment fails:

### Option 1: Revert Last Commit
```bash
git revert HEAD~1
git push origin main
```
GitHub Pages redeploys within 1-2 minutes.

### Option 2: Restore Previous Version
1. GitHub Pages → Settings → Logs
2. Find last successful deployment
3. Note commit SHA
4. Create revert PR referencing that SHA
5. Merge and deploy

### Option 3: Manual Hotfix
1. Create emergency branch: `git checkout -b hotfix/critical-issue`
2. Fix issue on branch
3. PR to `main` with urgent label
4. Fast-track review and merge
5. Deploy

---

## 7. Secrets & Environment Variables

**No secrets stored in repo.** Use:

- GitHub Secrets for API keys, tokens (if needed later)
- `cortexnexus@proton.me` email for support requests
- Config files excluded via `.gitignore`

Current `.gitignore`:
```
.env
.env.local
.DS_Store
node_modules/
*.log
```

---

## 8. Performance Optimization

### Image Optimization
```bash
# Install ImageOptim CLI or similar
imagemin *.{jpg,png} --out-dir=optimized/
```

### CSS Minification
```bash
# Via build script (optional, not required for static GitHub Pages)
npm install --save-dev cssnano postcss
```

### Lazy Loading
- Use `loading="lazy"` on images below fold
- Defer non-critical CSS/JS

### Caching
- GitHub Pages serves with HTTP caching headers
- Max-age: 5 minutes for HTML, 1 hour for assets

---

## 9. Domain & DNS

### Current Setup
- **Primary:** `cortexnexus.com` (CNAME → GitHub Pages)
- **GitHub Pages:** `cortex-nexus-sovereign-industrial-ai.github.io`

### DNS Records

| Type  | Name           | Value                                          |
|-------|----------------|------------------------------------------------|
| CNAME | cortexnexus.com | cortex-nexus-sovereign-industrial-ai.github.io |
| TXT   | _acme-challenge | [auto-generated by GitHub]                     |

Verify: `nslookup cortexnexus.com`

---

## 10. Maintenance & Updates

### Regular Tasks

**Weekly:**
- Check uptime monitoring alerts
- Review error logs

**Monthly:**
- Audit analytics
- Test backup/restore procedures
- Verify SSL certificate validity

**Quarterly:**
- Review performance metrics
- Assess capacity for growth
- Plan feature releases

### Updates to Files

1. Create feature branch: `git checkout -b feature/description`
2. Make changes
3. Test locally (open HTML files in browser)
4. Commit: `git commit -m "Describe change concisely"`
5. Push: `git push origin feature/description`
6. Create PR on GitHub
7. Request review from @mikecomplexai-7 or team
8. Merge to `main`
9. GitHub Actions deploys automatically

---

## 11. Troubleshooting

### Pages not deploying
- [ ] Check GitHub Actions tab for workflow errors
- [ ] Verify `main` branch protection rules not blocking
- [ ] Confirm `.html` files in root or correct folder

### Custom domain not working
- [ ] Verify DNS CNAME record propagated (`dig cortexnexus.com`)
- [ ] Check GitHub Pages settings still shows custom domain
- [ ] Wait 4-24 hours for full DNS propagation
- [ ] Contact domain registrar if CNAME not set

### Slow page loads
- [ ] Run Lighthouse audit
- [ ] Compress images
- [ ] Minimize CSS/JS (if bundling added)
- [ ] Check for render-blocking resources

### SSL Certificate errors
- [ ] Regenerate cert via GitHub Pages settings
- [ ] Contact GitHub Support if issue persists
- [ ] Verify domain ownership

---

## 12. Support & Escalation

**For deployment issues:**
- Email: `cortexnexus@proton.me`
- GitHub Issues: Tag `@mikecomplexai-7`

**For urgent outages:**
- 24/7 escalation via Wema Bank contact (if critical business impact)
- Post-incident review 48 hours after resolution

---

## Document Versioning

| Version | Date       | Changes                                    |
|---------|------------|--------------------------------------------|
| 1.0     | 2026-07-17 | Initial deployment guide                   |
| 1.1     | TBD        | Add monitoring dashboard integration       |
| 1.2     | TBD        | Add analytics tracking                     |

---

**Last updated:** 2026-07-17  
**Maintained by:** Michael Ujuku Morim (ARIA Strategic Assistant)  
**Contact:** cortexnexus@proton.me
