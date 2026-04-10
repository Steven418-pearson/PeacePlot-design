---
name: PeacePlot HTML Landing (blue-white)
overview: "Shipped single-file landing: travel-app–inspired blue/white UI (Inter, #F8F9FA, #2563EB), highlighted header slab, hero with wellness illustration + decorated motto, home/search/chips/popular, journey overlap card with stress + stats + tabs, sticky CTA, 5-tab nav. localStorage stress + toasts."
todos:
  - id: tokens-layout
    content: "Inter, blue primary, gray surfaces, card radii 24–28px, shadows"
    status: completed
  - id: header-hero-motto
    content: "Header-slab highlight; hero-motto image + gradient + motto card"
    status: completed
  - id: global-header-lockup
    content: "Logo + PeacePlot AI title aligned across landing and auth headers"
    status: completed
  - id: sections-scroll
    content: "Search, chips, popular cards, overlap journey card, sticky bar"
    status: completed
  - id: stress-js
    content: "peaceplot_stress_v1, stats sync, segmented tabs, 5-nav toasts"
    status: completed
isProject: true
---

# PeacePlot landing — `blue-white` bundle (as implemented)

This folder is the **self-contained** build: open [`index.html`](index.html) here so paths resolve to [`brain-hero.png`](brain-hero.png) and [`assets/hero-motto-bg.png`](assets/hero-motto-bg.png).

**Design origin:** Professional light mobile reference (travel-style cards, blue CTAs, generous radius). Copy and structure were adapted to **wellness / PeacePlot**, not travel destinations.

---

## Files in this bundle

| File | Purpose |
|------|---------|
| [`index.html`](index.html) | All markup, CSS, and JS (no build step). |
| [`sign-in.html`](sign-in.html) / [`sign-up.html`](sign-up.html) | Auth UI; [`auth.css`](auth.css) shared styles. |
| [`brain-hero.png`](brain-hero.png) | Thumbnail in “Popular” card and any brain imagery. |
| [`assets/hero-motto-bg.png`](assets/hero-motto-bg.png) | Full-width hero illustration (wellness / supportive-care art). |
| [`assets/images.jpeg`](assets/images.jpeg) | Optional extra asset (not required by `index.html`). |

---

## Global app header (implemented)

**Status:** Landing and auth now use the same brand lockup style and auth places the back control on the right side of the header.

1. **Every page** in this bundle that is part of the app experience (`index.html`, auth pages, any future screens) must include the **same primary header treatment** with:
   - **Logo** — the PeacePlot brand mark (same SVG / container as `.brand-logo` on the landing, unless replaced by a single shared asset later).
   - **Project title** — **`PeacePlot AI`** (matching the landing `brand-text` strong line; tagline *Calm · clarity · care* optional but should match landing if shown).
2. **Consistency** — Secondary actions (profile, back, bell) can vary by page, but **logo + title** stay in the same visual position and style as on the landing.

**Note:** Header persistence on scroll remains a future enhancement if desired.

---


## Global background image (implemented)

All `blue-white` pages now use `assets/nour-elhakim-CsiFAKKBwUc-unsplash.jpg` as the main page background with:

- `background-size: cover`
- `background-position: center`
- light overlay gradient for readability on cards and text

Applied in [`index.html`](index.html), [`auth.css`](auth.css) (for sign-in/sign-up), and [`search.html`](search.html).

---

## Visual system (implemented)

| Token | Value / usage |
|--------|----------------|
| Page background | `#F8F9FA` (`--bg`) |
| Cards / chrome | White (`--surface`), radius **24px** / **28px** hero |
| Primary | `#2563EB`, hover `#1D4ED8` |
| Text | Headings `#111827`, secondary `#6B7280` / `#9CA3AF` |
| Success | `#10B981` (badges, LOW stress) |
| Typography | **Inter** (Google Fonts): 400–700 |
| Icons | Thin stroke SVGs (~1.75px) in nav and UI |
| Shadows | Soft layered `box-shadow` on cards and bars |

---

## Page structure (top to bottom)

1. **Highlighted header (`.header-slab`)**  
   Wraps **`.site-header`**: **brand lockup** (`.brand-logo` SVG + **PeacePlot AI** + tagline *Calm · clarity · care*), profile menu. Gradient slab, rounded bottom corners, border and shadow.

2. **Hero + motto (`.hero-motto`)**  
   - **Image:** `assets/hero-motto-bg.png`, `object-fit: cover`, tuned `object-position`.  
   - **Overlays:** Layered gradient (bottom lift for readability + soft top/side).  
   - **Top controls:** Back circle, **★ 4.5** pill, **favorite** heart (toasts).  
   - **Motto block (bottom-left):** Frosted **glass** card with left **gradient accent bar**, typographic **quotes**, **“Doctor”** with blue→green **gradient text**, **“you”** with italic + violet→cyan **gradient**, **gradient rule**, **PeacePlot** line with green dot. *(Heart icon inside the motto card was removed per request.)*

3. **Search row**  
   Magnifier, readonly-style search placeholder, **filter** (toast).

4. **Categories**  
   Horizontal **chips:** Breathe, Sleep, Focus, Nature (toast on tap).

5. **Popular this week**  
   Two horizontal **cards**; first uses `brain-hero.png`, second gradient thumb; ratings and **Free / Pro** tags.

6. **Journey section (`.hero-block`)**  
   - **No** second full-bleed hero image here (removed after top hero shipped); content starts with **`.overlap-card`**.  
   - Title **Your guided calm journey**, pin + calendar meta, avatar strip + community line, **Ready** badge.  
   - **Stats grid:** Peace score (`#stat-peace`), Stress % (`#stat-stress-pct`), Streak **7d** — first two **sync from stress level** in JS.  
   - **Stress card:** Label + bar (`#stressLabel`, `#stress-fill`, `#stress-bar`); **Analyze your vibe** (`#btn-estimate`), **Personal recommendations** (`#btn-data`).  
   - **Segmented tabs:** Overview / Insights / Review — **static** panel swap via JS.

7. **Sticky CTA (`.cta-sticky`)**  
   Left: **Calm plan** + **Peace score · N** (`#sticky-summary`, live). Right: **Start journey** (`#btn-journey`).

8. **Bottom navigation (5 items)**  
   **Home** (filled vs outline icon when active), **Saved**, **Plan**, **Coach**, **Profile**. Non-home: `preventDefault` + **Coming soon** toast.

---

## JavaScript behavior

- **`localStorage` key:** `peaceplot_stress_v1` — `{ level: 0–100, at: ISO string }`.  
- **`setStress(level)`** updates stress label (LOW / MEDIUM / HIGH), bar width, **Peace score** (100 − stress, clamped), **stress %**, **sticky summary**.  
- **Toasts** (`#toast`): bell, filter, chips, hero back/heart, **btn-estimate** (“Vibe check saved.”), **btn-data**, **btn-journey**, secondary nav links.  
- **Tabs:** click sets `aria-selected` / `aria-hidden` on Overview · Insights · Review panels.

---

## Reference assets (historical)

Early mockups used a separate travel screenshot; the **shipped hero** uses the bundled **`assets/hero-motto-bg.png`** wellness illustration. Original reference PNGs may live only under Cursor project `assets/` and are **not** required in this folder.

---

## Out of scope (unchanged)

- No real routing, maps, or payments.  
- Search/chips/nav secondary items are **demo** interactions (toasts).

---

## Quick verify

1. Open `blue-white/index.html` in a browser from this directory.  
2. Confirm hero image and motto load; **Analyze your vibe** changes stress and stats.  
3. No console errors; `localStorage` updates after vibe check.

---

## Authentication pages (implemented)

Sign in / sign up with **Google** and **Microsoft** (full-color logos on buttons) plus **email** — see [`AUTH_PLAN.md`](AUTH_PLAN.md), [`sign-in.html`](sign-in.html), [`sign-up.html`](sign-up.html), and [`auth.css`](auth.css). Profile menu **Sign in** opens the sign-in page.
