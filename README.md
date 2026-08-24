# SiteAgent Status

Public status page for [SiteAgent], served by GitHub Pages: a single static `index.html`
rendering three live [Healthchecks.io](https://healthchecks.io) badges (app & dashboard,
chat connection, site monitoring) plus a hand-edited incident-notes section.

**Deliberately dumb** (launch-hardening plan §C2): no JavaScript, no vendors, no build step.
It must stay up — and stay honest — while the app's own hosting (Vercel), worker (Railway)
and database (Neon) are all down. That is its entire job.

## Editing incident notes

Edit the marked block in `index.html`, commit to `main`, and Pages republishes in about a
minute. Newest first; remove resolved notes after a few days.

## How the badges work

Each badge is a live SVG served by Healthchecks.io, driven by dead-man's-switch pings from
the SiteAgent worker (a missed ping flips the badge and emails the operator). The page never
talks to SiteAgent directly — during an outage the badges go red on their own.
