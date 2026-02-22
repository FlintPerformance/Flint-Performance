# Flint Performance — Claude.md

This file gives Claude context about the Flint Performance project so it can assist effectively across all pages and features.

---

## Project Overview

**Flint Performance** is a static 5-page website for a 1-on-1 online fitness coaching business targeting busy professionals. The brand identity is built around the concept of *the spark that starts the fire* — cold, disciplined, purposeful.

**Site is deployed on Netlify. Domain registered via Porkbun.**

---

## File Structure

```
/
├── index.html              # Landing page (homepage)
├── plan-checkout.html      # Coaching plan payment page (Stripe)
├── book-consult.html       # Phone consult booking + payment (Stripe)
├── flint-intake-form.html  # New client intake form (Formspree)
├── privacy-policy.html     # Privacy policy
└── CLAUDE.md               # This file
```

---

## Design System

### Fonts
- **Logo / Wordmark:** Barlow Condensed 900 — used only for `FLINT.` in nav and footer
- **Headings / Display:** Bebas Neue — all section titles, hero text, large labels
- **Body / UI:** DM Sans 300/400/500/600 — all body copy, buttons, form fields, navigation links

### Colors
```css
--black:     #060606   /* page background */
--white:     #ede8df   /* warm off-white, primary text */
--ember:     #f04a0e   /* primary brand accent — orange/fire */
--ember-hot: #ff6122   /* hover state for ember */
--ember-dim: #b83a0b   /* darker ember for active states */
--cold:      #b8ccda   /* secondary accent — steel blue/cold */
--gray:      #0e0e0e   /* section backgrounds */
--gray-mid:  #161616   /* card/field backgrounds */
--gray-up:   #222222   /* hover card backgrounds */
--muted:     #848484   /* secondary text */
--border:    rgba(237,232,223,0.06)  /* subtle dividers */
```

### Design Principles
- Sharp, cold, dark aesthetic — ember orange cuts through like a spark
- Minimal border-radius (2px max) — sharp edges throughout
- Heavy display typography contrasted with lightweight body copy (300 weight)
- Section padding: `120px 64px` desktop, `64px 20px` mobile
- No drop shadows except on ember CTAs (glow effect, not box shadow)

---

## Brand Voice

- **Tone:** Direct, disciplined, no fluff. Confident without being arrogant.
- **Target audience:** High-performing professionals — busy schedules, high standards, results-oriented
- **Key phrases / concepts:** "Built in the cold", "the spark that starts the fire", "discipline doesn't wait"
- **Avoid:** Motivational clichés, excessive exclamation marks, generic fitness language

### Flint Philosophy (manifesto copy — do not rewrite without instruction)
> *Cold. Hard. Unigniteable — until it's not.*
> Most people wait for motivation. Our clients create it. The gap between where you are and where you want to be doesn't close on its own — it closes when you strike the stone and commit to the fire.

---

## Pricing Structure

| Plan | Name | Price/mo | Key Features |
|------|------|----------|--------------|
| Level I | Foundation | $249 | Custom plan, monthly check-in, nutrition guidance |
| Level II | Momentum | $329 | Bi-weekly check-ins, enhanced nutrition, email support |
| Level III | Peak | $399 | Weekly check-ins, custom meal plan, unlimited messaging |

**Multi-month discounts:** 3mo = 5% off, 6mo = 10% off, 12mo = 15% off

**Phone consults:** 30-min Discovery Call ($75), 60-min Deep Dive ($135)

---

## Integrations

### Stripe
- **Mode:** Currently test mode. Switch to live key before launch.
- **Key location:** Hardcoded in `plan-checkout.html` and `book-consult.html`
- **Test publishable key:** `pk_test_51RlkLuG7...` (stored in both payment files)
- **⚠️ Important:** Payment collection is frontend-only (creates payment method). A backend endpoint is needed to create and confirm PaymentIntents server-side before going live. Netlify Functions recommended.
- **Stripe docs:** https://stripe.com/docs/payments/accept-a-payment

### Formspree
- **Used for:** Intake form submission
- **Endpoint:** `https://formspree.io/f/mnjbgvpy`
- **Location:** `flint-intake-form.html`

---

## Page Flow

```
Homepage (index.html)
├── Plan "Get Started" → plan-checkout.html?plan=1|2|3
│     └── After payment → Confirmation screen → flint-intake-form.html
├── "Book Now" (30min) → book-consult.html?session=30
├── "Book Now" (60min) → book-consult.html?session=60
└── Nav "Get Started" → plan-checkout.html
```

---

## Responsive Breakpoints

```css
/* Large desktop */
@media (min-width: 1280px)   /* expanded padding: 80px sides */

/* Tablet */
@media (max-width: 1024px)   /* single column layouts, reduced padding */

/* Mobile */
@media (max-width: 768px)    /* hamburger nav, stacked everything, 20px padding */

/* Small phone */
@media (max-width: 390px)    /* reduced font sizes */
```

**Mobile nav:** Hamburger menu opens a full-screen overlay with large Bebas Neue links.

---

## Known TODOs Before Launch

- [ ] Replace Stripe test key with live key (`pk_live_...`)
- [ ] Build backend endpoint (Netlify Function) to handle PaymentIntent creation server-side
- [ ] Update privacy policy contact email from `privacy@flintperformance.com` placeholder to real address
- [ ] Have attorney review privacy policy
- [ ] Test all Formspree submissions end-to-end
- [ ] Verify DNS propagation after Porkbun → Netlify nameserver update
- [ ] Set up SSL certificate on Netlify (auto-provisioned, just needs domain connected)

---

## Deployment

- **Host:** Netlify (drag and drop zip file)
- **Domain registrar:** Porkbun
- **Domain:** flintperformance.com (check availability)
- **DNS:** Point Porkbun nameservers to Netlify-provided nameservers
- **SSL:** Auto-provisioned by Netlify once domain is connected

---

## Working With This Codebase

- All pages are standalone HTML files — no build step, no framework, no dependencies
- CSS is inlined in each file's `<style>` block — keep it that way
- JavaScript is inline at the bottom of each file
- When editing styles, maintain the shared design system variables above
- Always test mobile (768px) and small phone (390px) breakpoints after changes
- The ghost FLINT lettermark in the hero uses `-webkit-text-stroke` — check Safari compatibility if modifying
