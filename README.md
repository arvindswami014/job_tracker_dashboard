# Nindo — Job Hunt Command Center

A phone-accessible dashboard for Arvind's UK job search: visa deadline countdown, weekly
application goal, ranked shortlist, GOV.UK sponsor watch, and follow-up reminders — themed
around Naruto characters (original artwork/mottos only, no reproduced show content).

**Live at:** enable GitHub Pages for this repo (Settings → Pages → Deploy from branch → `main` →
`/ (root)`) and it'll serve at `https://arvindswami014.github.io/job_tracker_dashboard/`.

## How it works

- `index.html` is a static page — no build step. On load it does a plain `fetch("./data.json")`
  and renders everything client-side.
- `data.json` is refreshed automatically twice a day by
  [job-hunter-agent](https://github.com/arvindswami014/job_tracker)'s `automation/run_scan.py`
  (via `automation/dashboard_export.py`), which commits and pushes **only this one file** —
  nothing else in this repo is ever touched by that automation.
- Sticky note and to-do list are stored in the browser's `localStorage`, keyed to this page's
  origin — they persist across visits and across `data.json` refreshes, but are private to
  whichever browser/device you used them on (not synced between devices).

## What's deliberately NOT here

This repo is public, so `data.json` only ever contains: company name, role title, job URL,
scores, resume-match %, and a `has_draft` boolean. It never contains phone number, email, full
job description text, or actual resume/cover-letter draft content — those stay local on Arvind's
PC in `job-hunter-agent/03_TAILORED_MATERIALS_/`.

## Files

- `index.html` — the whole dashboard (HTML/CSS/JS, self-contained)
- `data.json` — auto-refreshed snapshot, safe to regenerate/overwrite at any time
