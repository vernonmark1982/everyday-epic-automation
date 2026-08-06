# RISE 79 — Gumroad Product Deployment Checklist
## Products 1 & 3: 30-Day Launch Sequence — Days 1–20

---

## Days 1–3: Infrastructure First (no product built yet)

### MailerLite Account
- [ ] Create MailerLite account (free to 1,000 subscribers)
- [ ] Create ONE master list (name it: RISE79 Main List)
- [ ] Create interest tags: `nightshift-wealth`, `homegoing-kit`, `buyer-nightshift`, `buyer-homegoing`
- [ ] Verify sender email (valonbooks@gmail.com or a RISE79 branded address)

### Zapier Automations (2 Zaps required, set up before anything goes live)

**Zap 1 — Freebie Delivery**
- Trigger: New subscriber in MailerLite
- Filter: Tag contains "nightshift-wealth" OR "homegoing-kit"
- Action: MailerLite → Send email with freebie PDF link
  - Note: upload PDFs to Google Drive first; share a direct download link
  - Link structure: Drive → right-click → Get link → "Anyone with link can view"

**Zap 2 — Buyer Tagging**
- Trigger: New sale in Gumroad
- Filter: Product name contains "Nightshift" OR "Homegoing"
- Action: MailerLite → Add/update subscriber → Add tag: `buyer-[product]`
- Secondary action: MailerLite → Add to buyer sequence (Day 1 email fires immediately)

### GitHub Repos (Rise79 namespace)
- [ ] Create repo: `Rise79/nightshift-wealth` — push `products/nightshift-wealth/` contents
- [ ] Create repo: `Rise79/homegoing-tribute` — push `products/homegoing-tribute/` contents
- [ ] Each repo: `index.html` at root = ready for Cloudflare Pages

---

## Days 4–10: Build Products 1 and 3

### Product 1 — Nightshift Wealth System

**Lead Magnet PDF Assembly**
- [ ] Open `products/nightshift-wealth/lead-magnet-content.md`
- [ ] Assemble into PDF using Google Docs or Canva (fire palette, 8 pages)
- [ ] File name: `3-Day-Shift-Worker-Money-Reset.pdf`
- [ ] Upload to Google Drive → RISE79/OPS/nightshift-wealth/
- [ ] Get shareable download link → plug into Zapier Zap 1

**Gumroad Listing — Product 1**
- [ ] Open `products/nightshift-wealth/gumroad-listing.md`
- [ ] Create new Gumroad product → paste description text
- [ ] Price: $47 | Slug: `nightshift-wealth-system`
- [ ] Upload placeholder ZIP (or note that full content ships within 24hr of launch)
- [ ] Note the Gumroad product URL → update `href="#gumroad-cta"` in `index.html`

**Google Sheets Tracker**
- [ ] Build Rotation Budget Tracker in Google Sheets
  - Tab 1: 3×12 rotation template
  - Tab 2: 4×10 rotation template
  - Tab 3: 2-2-3 rotation template
  - Tab 4: Overtime calculator
- [ ] Share with "anyone with link can view" → add link to Gumroad product ZIP

**Full PDF (60 Pages)**
- [ ] Write using `gumroad-listing.md` "What's Inside" sections as chapter outline
- [ ] Assemble in Google Docs → export PDF
- [ ] RISE79 fire palette cover. Chapter headers in fire red. Body in white.

### Product 3 — Homegoing Tribute Creation Kit

**Lead Magnet PDF Assembly**
- [ ] Open `products/homegoing-tribute/lead-magnet-content.md`
- [ ] Assemble into PDF (6 pages, warm APEX palette)
- [ ] File name: `The-5-Minute-Obituary-Template.pdf`
- [ ] Upload to Google Drive → RISE79/OPS/homegoing-tribute/
- [ ] Get shareable download link → plug into Zapier Zap 1

**Gumroad Listing — Product 3**
- [ ] Open `products/homegoing-tribute/gumroad-listing.md`
- [ ] Create new Gumroad product → paste description text
- [ ] Price: $27 | Slug: `homegoing-tribute-creation-kit`
- [ ] Note Gumroad URL → update `href="#gumroad-cta"` in `index.html`

**Tribute Scripts + Obituary Templates (full product)**
- [ ] Write 20 tribute scripts (by relationship — use lead magnet as template base, expand)
- [ ] Write 10 obituary templates (short/standard/extended)
- [ ] Create 5 program layout PDFs (order of service structure)
- [ ] Assemble Sudden Loss Supplement (8 scripts)
- [ ] Assemble Relationship Modifier Guide
- [ ] Bundle into ZIP, upload to Gumroad

---

## Days 11–14: Domain + Cloudflare + MailerLite Forms

### Domain Setup (Hostinger → Cloudflare)
- [ ] Purchase nightshiftwealth.com via Hostinger (registrar only, NOT Horizon)
- [ ] Purchase homegoingkit.com via Hostinger
- [ ] In Hostinger: change nameservers to Cloudflare nameservers
  - Cloudflare account → Add site → Get nameservers → paste into Hostinger DNS settings

### Cloudflare Pages Deployment
- [ ] Connect GitHub to Cloudflare Pages
- [ ] Create project: `nightshift-wealth` → connect to `Rise79/nightshift-wealth` repo → deploy
  - Build settings: none (static HTML) | Root: / | Output: /
- [ ] Create project: `homegoing-tribute` → connect to `Rise79/homegoing-tribute` repo
- [ ] In Cloudflare: Custom Domain → enter Hostinger domain → follow verification steps
- [ ] Test: visit nightshiftwealth.com → should serve `index.html` from GitHub

### MailerLite Form Integration
- [ ] MailerLite → Forms → Create embedded form → "Nightshift Wealth Free Guide"
  - Fields: Email only (reduce friction)
  - After submit: redirect to "thank you" page OR show inline success
  - Add tag on subscribe: `nightshift-wealth`
- [ ] Copy embed code → replace the `<div class="form-wrap">` section in `index.html`
  - IMPORTANT: The `<div class="form-wrap">` wrapper and `.form-success` div are replaced by MailerLite's embed
  - Keep the `.magnet-box` wrapper (the gold-bordered card) — just replace the form inside it
  - Delete the `handleFormSubmit` JavaScript function after replacing with MailerLite embed
- [ ] Repeat for Homegoing Kit form
- [ ] Commit updated `index.html` to GitHub → Cloudflare auto-deploys

### Full Path Test (do this before any traffic)
- [ ] Mobile Chrome: visit nightshiftwealth.com → enter email → submit
- [ ] Check MailerLite → subscriber appears with correct tag
- [ ] Check Zapier → Zap 1 fires → freebie email arrives within 5 minutes
- [ ] Click Gumroad link in welcome email → product page loads → purchase flow works
- [ ] Make a $1 test purchase → check Zapier Zap 2 fires → buyer tag added in MailerLite

---

## Days 15–20: Pinterest Launch

### Product 1 Pinterest Pins (3 pins)
Copy from `products/nightshift-wealth/gumroad-listing.md` → Pinterest Pin Copy section

- [ ] Pin 1: Problem pin (fire palette graphic) → link to nightshiftwealth.com
- [ ] Pin 2: Pain point pin → link to nightshiftwealth.com
- [ ] Pin 3: Authority pin → link to nightshiftwealth.com
- [ ] Schedule via Buffer: 1 pin/day for 3 days
- [ ] Image size: 1000×1500px (Pinterest vertical format)
- [ ] Design: APEX fire palette — obsidian bg, fire accent, gold text, white body

### Product 3 Pinterest Pins (3 pins)
Copy from `products/homegoing-tribute/gumroad-listing.md` → Pinterest Pin Copy section

- [ ] Pin 1: Search traffic pin → homegoingkit.com
- [ ] Pin 2: Distinction pin → homegoingkit.com
- [ ] Pin 3: Emotional pin → homegoingkit.com
- [ ] Schedule via Buffer: staggered 2 days apart

### Week 2 Signal Check (Day 22)
- [ ] Review nightshiftwealth.com traffic (Cloudflare Analytics)
- [ ] Count email signups in MailerLite
- [ ] If conversion rate below 30% of landing page visitors → rewrite hero headline only
- [ ] If above 30% → begin Product 4 (Night Frequency) build

---

## Day 30 Kill Criteria (non-negotiable)

**Continue if any ONE of these is true:**
- 3+ paying Gumroad customers across Products 1 and 3 combined
- 200+ email subscribers in MailerLite
- 1 returning buyer (proof of repeat purchase mechanism working)

**Revise (not stop) if:**
- High email signups + zero Gumroad sales → the product page or price is the problem. Rewrite the Gumroad description. Test $37 vs $47 for Product 1.

**Stop a product (not the system) if:**
- 100+ clicks to the Gumroad listing → zero purchases → replace that product listing with Product 2 or Product 5 from the portfolio.
- Do not drop the price. Replace the product.

---

## Quick Reference: File Locations

| Asset | Location |
|-------|----------|
| Nightshift Wealth landing page | `products/nightshift-wealth/index.html` |
| Nightshift Wealth Gumroad copy | `products/nightshift-wealth/gumroad-listing.md` |
| Nightshift Wealth lead magnet | `products/nightshift-wealth/lead-magnet-content.md` |
| Homegoing Tribute landing page | `products/homegoing-tribute/index.html` |
| Homegoing Tribute Gumroad copy | `products/homegoing-tribute/gumroad-listing.md` |
| Homegoing Tribute lead magnet | `products/homegoing-tribute/lead-magnet-content.md` |
| This checklist | `products/DEPLOYMENT-CHECKLIST.md` |
| Full 10-product playbook | RISE 79 Gumroad Empire Playbook (artifact) |

---

**No people contact required. Gumroad delivers. Zapier notifies. MailerLite follows up.**
**The machine runs while the shift runs.**
