# Sajda Legal Website

A small, static legal website for the Sajda Islamic Application, built for
GitHub Pages hosting and the Google Play Store listing.

## Pages

| Path | Purpose |
|---|---|
| `/` | Landing page with links to the Privacy Policy and Account Deletion pages |
| `/privacy/` | Sajda Privacy Policy |
| `/delete-account/` | Account deletion instructions (publicly accessible, no login required) |

## Technology

Plain HTML, CSS, and no JavaScript. No build step, no frameworks, no
analytics or tracking scripts. Shared styles live in `assets/styles.css`.
System fonts are used (no font-hosting dependency).

All internal links are relative (`./`, `../`) so the site works correctly
whether it's hosted at a domain root or at a GitHub Pages project path like
`https://USERNAME.github.io/sajda-legal/`.

## Branding

The official Sajda logo lives at `assets/sajda_app_branding_logo.png`
(transparent PNG, 1448×1086, ~4:3 aspect ratio) and is used consistently
across all three pages:
- A compact version in the sticky nav header (`.brand-mark`, ~40px tall,
  32px on narrow screens), linking back to the home page.
- A larger version in the home page hero (`.hero-geo`, responsive up to
  280px wide, capped at 200px on small screens).

The logo is never cropped or stretched — only `height`/`max-width` is
constrained in CSS, with `width: auto` so the browser preserves the
source aspect ratio. Every instance uses `alt="Sajda"`.

## Source of content

The Privacy Policy and Account Deletion content was written from a direct
review of the actual Sajda Flutter app source
(`lib/features/legal/screens/privacy_policy_screen.dart`, `pubspec.yaml`, and
the Contact Us flow), found at `~/Desktop/islamic_app-main` on this machine,
so the web copy does not contradict the in-app policy. The app's own privacy
screen is itself marked as a development draft that hasn't had legal review —
several items below are flagged there as unresolved, and are carried over to
this checklist.

Verified from the app's code:
- Firebase Authentication (email/password + Google Sign-In), Cloud Firestore,
  and Firebase Cloud Messaging are active dependencies.
- No analytics, crash-reporting, or advertising SDK is present in `pubspec.yaml`.
- Location (`geolocator`/`geocoding`) and camera (`camera`) are used only in
  the foreground, for prayer-time/Qibla calculation and the Qibla AR camera
  overlay respectively — not uploaded or recorded.
- There is no self-service "Delete my account" action in the app; deletion
  today goes through the in-app Contact Us form.

## Support email

The confirmed support/contact email for this site is
**ahmadejaz2446@gmail.com**. It's used as a clickable `mailto:` link in:
- `privacy/index.html` — Contact Us section.
- `delete-account/index.html` — the manual deletion request steps, the
  Questions section, and the "Request Account Deletion" CTA button (with
  the subject pre-filled to `Sajda Account Deletion Request`).

## BEFORE PUBLISHING

- [ ] **Confirm the account deletion process.** The app currently has no
      in-app self-service deletion button; this site documents a manual
      email-request flow. If a self-service flow is added to the app later,
      update `delete-account/index.html` to match.
- [ ] **Define a data retention period** for data kept after account
      deletion (and generally). This is not yet defined anywhere in the app
      or policy — `privacy/index.html` and `delete-account/index.html` both
      flag this with a conservative "not yet finalized" notice instead of
      inventing a number (e.g. 30/90 days).
- [ ] **Finalize a Children's Privacy policy** (age restrictions, parental
      consent if applicable) — not yet defined by the app/publisher.
      `privacy/index.html` currently flags this as unresolved rather than
      asserting a position.
- [ ] **Confirm the "Last updated" date** in `privacy/index.html` before
      publishing — it's currently set to the date this site was generated,
      but the app's own privacy screen has never had a confirmed effective
      date for any prior version.
- [ ] **Review this policy against your final Google Play Data Safety form
      answers** so the two stay consistent (data collected, data shared,
      security practices, deletion request mechanism).
- [ ] **Verify all links** work once hosted (see below).

## Verifying links after deployment

Once pushed to GitHub Pages, confirm:
- `https://USERNAME.github.io/sajda-legal/` loads the home page.
- Both cards on the home page navigate correctly to `/privacy/` and
  `/delete-account/`.
- Each page's nav links (Home, Privacy Policy, Account Deletion) resolve
  correctly and the current page is highlighted.
- The `mailto:` button on the Account Deletion page opens mail correctly
  addressed to ahmadejaz2446@gmail.com with the subject pre-filled.
- The logo loads correctly on all three pages at its relative path
  (`./assets/...` from `/`, `../assets/...` from `/privacy/` and
  `/delete-account/`).

## What this repo intentionally does NOT include

- No git initialization, remotes, or commits — handled manually by the
  project owner.
- No GitHub repository creation or push.
- No GitHub Pages deployment configuration.
- No analytics, tracking, or third-party scripts of any kind.
# sajda-legal
