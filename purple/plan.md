# PeacePlot — purple landing (night / glass)

## Intent

Single-file landing in [`index.html`](index.html) with **dark celestial** UI (inspired by premium sleep-app references in `assets/*.avif`), **PeacePlot AI** branding, hero motto + illustration, **two primary actions**, slides, common sense, forum/media block, analytics snapshot, **four-item dock**, and **profile menu** with sign in/out.

## Visual system (sample-aligned)

- **Background:** Base `#0b0e1b`. Layers: **Unsplash** smooth gradient still (`photo-1579546929518` — soft, low visual noise) under **gentle** violet / lavender / cyan washes, **bottom vignette**, and **vertical wash**. **::before** very soft highlight **drift** (disabled if `prefers-reduced-motion`). **::after** sparse **stars** (low opacity). Offline: solid + gradients still read if the image is blocked.
- **Glass:** `backdrop-filter` 18–24px, borders `rgba(255,255,255,0.1)`, **inset top highlight** on cards, dock, and primary chrome.
- **Hero:** **Short fixed height** `clamp(7.25rem, 26vw, 9.75rem)`; **inner shine** (`screen` blend) + dark **legibility veil**; motto **Plus Jakarta Sans**, restrained size; sublabel **PeacePlot AI** only.
- **CTAs:** Estimate = purple→magenta gradient + **glow** + inset highlight; Forum = frosted glass pill.
- **Data viz:** Stress bar and chart bars = **cyan→mint** with light **glow** (reference chart look).

## Structure (top → bottom)

1. **Header** — Left: logo mark + **PeacePlot AI** + kicker “Calm · clarity · care”. Right: **profile** control; opens **dropdown** (Sign in/out, Account & security, Notifications, Help & support, About). Guest shows **line user icon**; signed-in shows **ui-avatars** (or **initial** on error). State: `localStorage` `peaceplot_user_v1`.
2. **Hero** — `assets/hero-motto-bg.png` in **short** frame; shine + veil; motto **Doctor is behind you!** (`you` weighted), subline **PeacePlot AI**.
3. **Action row (2)** — **Estimate stress** (updates stress + scrolls to panel); **Calm picks & forum** (scrolls to forum + toast).
4. **Stress card** — Bar, LOW/MEDIUM/HIGH, %; syncs with `peaceplot_stress_v1`.
5. **Featured** — Horizontal **slides** (3 glass cards).
6. **Common sense** — Three **tip rows** with icons.
7. **Forum / media** — `#forum` heading + three placeholder links (toast).
8. **Analytics** — Two **stat tiles** (calm score from stress; streak static demo) + **mini bar chart** (decorative).
9. **Dock (4)** — Home (current), Insights, Analytics, More → non-home toasts.

## JavaScript

- `peaceplot_stress_v1` — stress 0–100, persists on estimate.
- `peaceplot_user_v1` — `{ signedIn, name }`; toggle via menu **Sign in** / **Sign out** (demo name “Alex Morgan”).
- Dropdown: backdrop click + **Escape** closes; `aria-expanded` on trigger.
- Toasts for nav, menu items, forum links, brand scroll-top.

## Assets

- [`assets/hero-motto-bg.png`](assets/hero-motto-bg.png) — hero image.
- [`brain-hero.png`](brain-hero.png) — optional (not used in current `index.html`; keep for future).

## Status

- [x] Plan reflects shipped purple landing.
