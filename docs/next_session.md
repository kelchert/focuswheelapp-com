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
- **Netlify auto-deploy webhook — OPEN, low priority.** Didn't fire on a PR merge; had to
  Trigger deploy manually. Cause unknown — check the GitHub→Netlify webhook delivery log /
  build-hook config next site session. Will recur on the next site change if unfixed.
- **Post-merge form check (one-time) — OPEN.** Confirm `android-notify` detection in the
  Netlify Forms dashboard + one production test submission lands under Forms → android-notify.
- **Android-launch list (FW pool) — collect-only.** The `android-notify` form is the FW
  Android-launch capture pool. No ESP/export wiring yet; pick a send tool (MailerLite free
  candidate) when FW Android ships, then export this pool and send the announcement. Twin
  pool on deepalignment.com is `da-android-notify` (separate, no reconciliation).

## Parked
- OG/preview and copy are settled; no design work queued.
