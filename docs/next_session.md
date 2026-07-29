# focuswheelapp-com — Next Session

Living handoff. Read at session start, update at session close. This repo is a sibling under
the [FW] seat — keep this current so [FW]'s rollup (→ DAC) can read it.

## Human status — focuswheelapp-com (seat's read, as-of 2026-07-14)
Onboarded into the doc-architecture today as a governed sibling repo (repo-local CLAUDE.md +
this handoff), following the FocusWheel-android precedent — the site had been taking commits
ad hoc with no spine. Nothing is in-flight on the site itself: the Android-notify capture
form is live, the /roots Abraham page shipped, and the OG/canonical link-preview fix is
merged and verified. Two small things stay open, neither blocking: the Netlify auto-deploy
webhook didn't fire on the last PR merge (had to Trigger deploy by hand), and the one-time
post-merge form check on `android-notify` still needs doing in the Netlify dashboard.

## Current state (compact)
`main`, in sync with `origin`. HEAD `f0d4b8e` (PR #3 — privacy-policy Android wording). The
site is live and stable; SEO/OG/JSON-LD metadata hand-maintained per page; Netlify serves
from repo root (`publish = "/"`).

## Shipped (durable milestones, most recent first)
- **Privacy-policy Android wording** (`f0d4b8e`, PR #3) — merged.
- **OG/canonical anchored to apex** (`0e5f8f6`, PR #2, merged 2026-06-15) — resolved the
  www/apex contradiction that made Messenger previews non-deterministic; both pages verified
  apex-clean in the Sharing Debugger, production cache warmed. Decision recorded in CLAUDE.md.
- **Android notify-me form + /roots Abraham page + splash entry point** (`fa2c54e`,
  repositioned `fb0c6a0`; PR #1 `b25dc06`) — the `android-notify` Netlify Form (email capture
  for the FW Android launch), the `/roots` Abraham-Hicks resource page, and the splash entry.
- **Self-hosted og:image, brand-world treatment, SEO metadata/sitemap/robots** (`962eb15`,
  `18e52c4`) — foundation.

## Open threads
- **Google Play badge — STAGED, HELD, do not merge yet.** Branch
  `feat/google-play-badge`. Adds the Play badge beside the App Store badge in both hero
  and closing CTAs, retires "Android coming soon", repurposes the `android-notify`
  capture to general updates ("New from Resurface" / "Keep me posted"), and moves the
  price note under the badges it qualifies.
  **Trigger to publish: Resurface: Deep Alignment going live on Android** (Kenn-ruled
  2026-07-29). Publish = merge to `main`; Netlify deploys on merge — and per the open
  webhook thread, be ready to Trigger deploy by hand.
  ⚠️ Until merged, the live page still says "Android coming soon", which has been false
  since FW Android shipped 2026-07-29.
  Netlify form name deliberately unchanged (`android-notify`) so the existing submission
  record is not split — revisit only if the stale name becomes confusing.
- **Netlify auto-deploy webhook — OPEN, low priority.** Didn't fire on a PR merge; had to
  Trigger deploy manually. Cause unknown — check the GitHub→Netlify webhook delivery log /
  build-hook config next site session. Will recur on the next site change if unfixed.
- **Post-merge form check (one-time) — OPEN.** Confirm `android-notify` detection in the
  Netlify Forms dashboard + one production test submission lands under Forms → android-notify.
- **Android-launch list (FW pool) — CONDITION MET, SEND GATED, do not send.**
  **Trigger CONDITION MET:** Focus Wheel Android shipped to Google Play 2026-07-29.
  **SEND IS GATED — do not send yet.** Two reasons, both Kenn-ruled 2026-07-29:
  (a) no promotion of FW-Android until Resurface-Android is also live; (b) FW-Android
  ships copy naming Resurface as an available companion app with a $49.99 lifetime
  tier, ACCEPTED as-is specifically because exposure would be stumble-upon only —
  sending this pool converts stumble-upon into directed traffic and invalidates the
  premise the accept-ruling rests on.
  **RELEASE CONDITION:** Resurface-Android live on Google Play — the same event that
  releases the held `feat/google-play-badge` branch.
  **Do not treat "condition met" as "cleared to send." They are separate facts and
  this entry must not collapse them again.**
  **Pool segmentation, load-bearing for whenever this does send:** the `android-notify`
  Netlify form now serves two distinct cohorts under one submission record.
  Submissions BEFORE 2026-07-29 opted in to "Android coming soon / Notify me" — a
  request to be told when Focus Wheel Android shipped. Submissions ON OR AFTER
  2026-07-29 opted in to "New from Resurface / Keep me posted" — general updates. The
  form name was deliberately NOT renamed (renaming creates a new Netlify form and
  splits the existing submission record, which `CLAUDE.md` names as the system of
  record). **The submission timestamp is the only discriminator** between the two
  cohorts — any export treating the pool as homogeneous will conflate them. The
  pre-2026-07-29 cohort consented to an Android-launch notification specifically, not
  to general marketing; honor the narrower scope for that group when sending.
  No ESP/export wiring yet; pick a send tool (MailerLite free candidate) once the
  release condition is met. Twin pool on deepalignment.com is `da-android-notify`
  (separate, no reconciliation).
  **Deploy verification (2026-07-29):** the copy fix (`bec7cfa`) is committed, pushed,
  and **confirmed live** on focuswheelapp.com — cache-busted fetch, server `date`
  header confirmed fresh. "Android coming soon" / "Notify me" / "we'll let you know
  when Android lands" are gone from the live page. **The cohort boundary above is
  therefore TRUE as written: 2026-07-29 is the actual cutover date.**
  Build-hook status: the parked build-hook concern did **not** block this deploy.
  Unknown whether it did not recur or whether something else got the build out — no
  credentialed Netlify access from CC to distinguish. **Leaving that parked item OPEN.**
  Form detection: the deployed `<form>` tag has `data-netlify` and `netlify-honeypot`
  stripped and its attributes rewritten — Netlify's own build-time form-processing
  signature (an undetected form ships through unmodified). Strong indirect evidence the
  form re-registered this build, but **this is not the parked check** — dashboard
  registration plus a live test submission landing under Forms → android-notify remains
  **owed, Kenn's to do. Leaving that parked item OPEN.**

## Parked
- OG/preview and copy are settled; no design work queued.
