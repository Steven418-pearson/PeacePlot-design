# PeacePlot — Sign in & Sign up (`blue-white`)

**Status:** **Implemented** (static UI + placeholder toasts; OAuth/email backend TBD).

---

## Goals (met)

1. Two pages — [`sign-in.html`](sign-in.html) and [`sign-up.html`](sign-up.html) — match the landing look (Inter, `#F8F9FA`, `#2563EB`, white cards, soft shadows, `max-width` shell).
2. **Both pages include:**
   - **Continue with Google** — full-color **Google “G”** logo (official palette: blue, green, yellow, red) in the button.
   - **Continue with Microsoft** — **Microsoft four-square** logo (official red, blue, green, yellow tiles).
   - **Email + password** (sign-up adds **confirm password** + **Terms** checkbox).
3. **Shared stylesheet:** [`auth.css`](auth.css) so both pages stay visually identical for OAuth rows, forms, and toast.
4. Cross-links: sign-in ↔ sign-up; **Home** returns to [`index.html`](index.html).
5. Profile menu **Sign in** opens [`sign-in.html`](sign-in.html) (no instant demo sign-in from the menu).

---

## Files

| File | Role |
|------|------|
| [`sign-in.html`](sign-in.html) | Sign-in: Google, Microsoft, email form, forgot password stub. |
| [`sign-up.html`](sign-up.html) | Sign-up: same OAuth row + email, confirm password, terms. |
| [`auth.css`](auth.css) | Shared tokens and components for auth pages. |

**Brand logos:** Embedded inline SVGs (not external images) so they work offline and stay sharp. Colors follow commonly used Google / Microsoft identity colors for the standard “G” and four-square marks.

---

## Behavior (current)

- **Google / Microsoft:** toast explaining server connection is required later.
- **Email submit:** toast; sign-up validates non-empty fields, **password match**, and **terms** checked.
- **Forgot password / Terms links:** toast placeholders.

---

## Future

- Wire OAuth and email to your backend or Auth provider.
- Replace toasts with real redirects and error states.

---

## Alignment with global header (pending)

Sign-in and sign-up currently use a minimal **`auth-header`** (Home link + “PeacePlot AI” text). Per **[`LANDING_PLAN.md`](LANDING_PLAN.md)** — *Global app header*, they should be updated **when approved** to reuse the **same logo + PeacePlot AI title** (and sticky behavior) as the landing so brand presence is consistent on every page. No code changes until the user says **go**.

---

## Checklist

- [x] `sign-in.html` & `sign-up.html` + `auth.css`
- [x] Google + Microsoft logos visible on both OAuth buttons
- [x] Email flows on both pages
- [x] Cross-links + Home
- [x] Profile **Sign in** → `sign-in.html`
