# focuswheelapp-com — CLAUDE.md

The FocusWheel marketing/landing site (focuswheelapp.com). Static HTML/CSS, Netlify-hosted.
Sibling repo under the [FW] seat; reports to DAC. Not a port and not the app — this is the
web property. No parity target; the app repos (`~/Developer/FocusWheel`,
`kelchert/FocusWheel-android`) are separate seats.

## Session start (read first)
<!-- Intentionally a top-level section, not nested under Workflow: reading the shared docs
is portfolio-level policy (see deepalignment-docs/docs/DOC_ARCHITECTURE.md), a different
scope than this repo's workflow rituals. Do not flatten without revisiting that scope. -->
1. `git pull` the `~/Developer/deepalignment-docs` clone; read `docs/START_HERE.md` (hub
   index), `docs/DOC_ARCHITECTURE.md` (charter), `docs/COLLABORATION.md` (claude.ai
   disciplines — Kenn relays this into the claude.ai session), `docs/SESSION_RITUAL.md`
   (the open/close procedure — **run it**), and `docs/OUTSTANDING.md` / any handoff briefs
   relevant to this work. **To start, the human says: "run the session open ritual"; to
   end: "run the session close ritual."**
2. Read this repo's `docs/next_session.md` — the canonical handoff (current standing +
   owed work).
3. Precedence: the repo is canonical. No claude.ai-side or panel copy overrides an on-disk
   doc. Pull before reading; pull before push.

## What this repo is
The static site served at focuswheelapp.com. Plain HTML/CSS (no build step, no framework),
deployed by Netlify straight from the repo root (`netlify.toml` → `publish = "/"`). Pages:
`index.html` (home), `roots/` (the Abraham-Hicks resource page), `faq/`, `support/`,
`privacy-policy/`, plus `sitemap.xml`, `robots.txt`, and the Google Search Console
verification file. An Android-launch email-capture form (`android-notify`, a Netlify Form)
lives on the home page near the App Store badge; SEO/OG/JSON-LD metadata is hand-maintained
in each page's `<head>`.

## Deploy
Netlify auto-deploys on merge to `main` (webhook — see `docs/next_session.md` for the
still-open reliability issue where it didn't fire on a PR merge and needed a manual
Trigger deploy). `netlify.toml` disables email obfuscation. After any OG/canonical/metadata
change, verify with Facebook's Sharing Debugger and warm the production cache — the site
serves at apex; canonical + og:url + JSON-LD url must stay apex-consistent (see Decisions Log).

## Data boundary
Form submissions are the system of record in the **Netlify Forms** dashboard, never mirrored
here. `publish = "/"` means the whole repo root is a publication surface: anything present in
the tree ships on deploy, so keep non-public material out of the repo entirely (gitignore
alone does not stop a folder-root deploy — the portfolio publish-root lesson).

## Workflow (per COLLABORATION.md — the base layer, not restated here)
- claude.ai ([FW] seat) designs/decides/specs; CC applies all file + git work; Kenn gates.
- Audit-first before any change; one-task-one-commit; the approval-before-commit gate is
  absolute.
- Verification for a site is the deployed page, not the local file: OG/preview changes are
  proven in the Sharing Debugger; form changes in the Netlify Forms dashboard.

## Current state
Branch-state records the **sync condition** (e.g. "main, in sync with origin"), never the
self-HEAD SHA. The rolling state — what shipped, what's in-flight, what's owed — lives in
`docs/next_session.md`, refreshed every session close. Read it for current standing; this
file holds the durable spine, not the moving state.

<!-- Project-specific sections (page conventions, decisions log) added below as the work
surfaces them — not front-loaded. -->

## Decisions Log

### 2026-06-15 — OG/canonical anchored to apex (`0e5f8f6`, PR #2)
The www/apex contradiction that made Messenger link-previews non-deterministic (worked in
iMessage, flickered in Messenger) was resolved by pointing canonical + og:url + JSON-LD url
at the apex host on the front page and `/roots`. Standing rule: keep every canonical/og:url/
JSON-LD url apex-consistent on new pages, or link previews regress.
