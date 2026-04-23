# Guidance Funding Website — Static Site Archive

Archive date: **April 23, 2026**

Static multi-page site for **guidancefunding.com**, deployed on GitHub Pages with a custom domain. Structured as folder-per-page for clean URLs (no `.html` in the address bar).

## Structure

```
repo-root/
├── index.html               → guidancefunding.com/
├── styles.css               (shared stylesheet, loaded via /styles.css)
├── CNAME                    (custom domain config for GitHub Pages)
├── apply/index.html         → guidancefunding.com/apply/
├── contact/index.html       → guidancefunding.com/contact/
├── bridge/index.html        → guidancefunding.com/bridge/
├── loc/index.html           → guidancefunding.com/loc/
├── term/index.html          → guidancefunding.com/term/
├── equipment/index.html     → guidancefunding.com/equipment/
├── mortgage/index.html      → guidancefunding.com/mortgage/
├── po/index.html            → guidancefunding.com/po/
├── sba/index.html           → guidancefunding.com/sba/
├── factoring/index.html     → guidancefunding.com/factoring/
├── credit-services/index.html → guidancefunding.com/credit-services/
├── ccp/index.html           → guidancefunding.com/ccp/
├── bookkeeping/index.html   → guidancefunding.com/bookkeeping/
├── seo/index.html           → guidancefunding.com/seo/
└── payroll/index.html       → guidancefunding.com/payroll/
```

## Deployment

1. Push everything in this archive to your GitHub repo root
2. In repo Settings → Pages, confirm the custom domain reads `guidancefunding.com`
3. In your DNS provider, ensure an `A` or `CNAME` record points to GitHub Pages servers (185.199.108.153 / .109.153 / .110.153 / .111.153 for apex, or `<username>.github.io` for CNAME on www subdomain)
4. Enable "Enforce HTTPS" in GitHub Pages settings once the domain is verified
5. Hard refresh (Cmd+Shift+R) after push

## Key URL conventions

- All internal links use **root-relative paths** with trailing slashes: `href="/bridge/"` not `href="bridge.html"`
- The stylesheet is loaded via `/styles.css` so it works from every subfolder
- Same-page anchors on the homepage are still supported: `/#calculator`, `/#faq`, `/#testimonials`
- The `CNAME` file contains exactly: `guidancefunding.com`

## Design System

- **Fonts:** Outfit (display headings), DM Sans (body), Montserrat (apply form only)
- **Colors:** `#12948A` (teal), `#0A5D57` (dark teal), `#073F3A` (deep teal), `#F5A623` (amber)
- **Ink:** `#0f1729` / Body text: `#475467`

## Contact info (baked into every page footer)

- Phone: `(213) 522-7765`
- Email: `admin@guidancefunding.com`
- Location: Beverly Hills, CA
- Hours: Monday–Friday, 7am–7pm PST
- License: California Lenders License #60DBO 67237

## Pending items

- **Calendly/booking link** for `contact/index.html` — "Book a call" button currently `href="#book-link-placeholder"`
- **MyRM redirect** — `apply/index.html` form submit currently alerts + logs to console. To enable redirect, uncomment near end of `<script>`:
  `// window.location.href = 'https://apply.myrmapp.com/multi-step-apply/lisagl';`

## Edit tips

- **Nav and footer are duplicated in every page.** To change nav/footer, edit every file. `sed` across folders:
  ```
  find . -name "*.html" -exec sed -i 's|OLD|NEW|g' {} +
  ```
- **styles.css affects 16 pages** (everything except index.html). Homepage has inline CSS and must be updated separately.
- **Mobile breakpoints:** 1100px, 960px, 560px, 420px. Hamburger appears at 960px.
- **Deleting a page:** remove the folder. No other cleanup needed — root-relative links make it self-contained.

## Known conventions

- All "Apply Now" / "Apply Online" buttons point to `/apply/`
- Bridge loan product is structurally the same product as a merchant cash advance. Check with counsel about disclosures if unsure about the branding change.
