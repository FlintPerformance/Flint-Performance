# Flint Performance — Claude.md

This file gives Claude context about the Flint Performance project so it can assist effectively across all pages and features.

---

## Project Overview

**Flint Performance** is the homepage and brand hub for a family of fitness-themed web apps. Each app lives on its own subdomain under `flintperformance.com`. The brand identity is built around the concept of *the spark that starts the fire* — cold, disciplined, purposeful.

**Site is deployed on Netlify. Domain registered via Porkbun.**

---

## The App Family

| App | Subdomain | Description | Status |
|-----|-----------|-------------|--------|
| CYCLE. | cycle.flintperformance.com | PED/steroid cycle logger — compounds, blood work, reminders, PK charts | Live |
| CALC. | calc.flintperformance.com | Fitness calculator — 1RM, TDEE, macros, body fat | Live |
| SCALE. | scale.flintperformance.com | Weight logging — daily weigh-ins, trend tracking | Coming Soon |
| LIFT. | lift.flintperformance.com | Weight lifting log — sets, reps, progression | Coming Soon |
| DIET. | diet.flintperformance.com | Food tracking — meals, macros, daily targets | Coming Soon |

Each app uses the Barlow Condensed 900 wordmark style (e.g. `CYCLE.` with the ember-colored dot) on a black background for its icon, matching the `FLINT.` brand identity.

---

## File Structure

```
/
├── index.html              # Homepage — app family showcase
├── privacy-policy.html     # Privacy policy
└── CLAUDE.md               # This file
```

---

## Design System

### Fonts
- **Logo / Wordmark / App Icons:** Barlow Condensed 900 — used for `FLINT.`, `CYCLE.`, `SCALE.`, `CALC.`, `LIFT.`, `DIET.` branding
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
- App icon style: Barlow Condensed 900 text over black background, rounded corners (18px), ember dot

---

## Brand Voice

- **Tone:** Direct, disciplined, no fluff. Confident without being arrogant.
- **Target audience:** People who train with intention — focused, results-oriented, no tolerance for bloat
- **Key phrases / concepts:** "One purpose per app", "sharp tools", "built to do one thing and do it right"
- **Avoid:** Motivational clichés, excessive exclamation marks, generic fitness language, feature bloat

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

## Deployment

- **Host:** Netlify (drag and drop zip file)
- **Domain registrar:** Porkbun
- **Domain:** flintperformance.com
- **Subdomains:** Each app is a separate Netlify site pointed to its subdomain
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
