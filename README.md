# Marco Furnari

**I make platforms talk to each other.**

Eleven years in web operations, MarTech and API integrations — most of it spent on the unglamorous seam between systems that were never designed to work together: a hosted LMS and a WordPress site, a CRM and a checkout, a marketing stack and a database that has to stay consistent at the end of the month.

I've been on both sides of that seam. I've built the integrations, and I've been the customer who had to live with them — running an online school, shipping client sites, and doing the technical SEO work that pays for none of it but breaks all of it. That has shaped how I work more than any framework has.

---

## What I do

- **Integrate platforms that don't share identity or data.** Webhooks, REST APIs, signed single sign-on, idempotent syncs, and the reconciliation you need for when a webhook silently doesn't arrive.
- **Work in WordPress at the level that matters.** Custom plugins, the REST API, `$wpdb`, cron, capabilities — and the security review that should come with all of it.
- **Automate what people are doing by hand.** Crawling, parsing, extraction, reporting — usually in Python, usually because someone was copying numbers into a spreadsheet every Monday.
- **Translate between engineering and the business.** Scoping what should *not* be built is the part of the job I'm best at, and the part clients thank me for a year later.

---

## Selected work

### [lms-wp-bridge](https://github.com/Furnari-Marco/lms-wp-bridge) — LMS ↔ WordPress bridge

A WordPress plugin connecting a hosted LMS (Teachable-style) to a WordPress site: enrollments and sales mirrored through authenticated webhooks, single sign-on over HMAC-signed single-use links, lecture-level activity tracking, and behavioural detection of shared accounts and automated course downloads.

What it demonstrates:

- **A real threat model, not a checklist.** Signed redirects, single-use tokens, constant-time comparison, SSO that refuses to authenticate privileged accounts, and staged webhook enforcement so a live integration can be hardened with zero downtime.
- **Detection that survives evasion.** Download tools now drive genuine, "undetected" browsers. The detectors combine signals those tools can't cheaply fake — trusted interaction counts, visible time, referrer presence, curriculum coverage per session — instead of trusting a client-side automation flag.
- **Storage designed for years of history.** ~65 bytes per activity row, packed binary IPs, batched retention that never locks the table.
- **90 tests** (77 PHP, 13 JavaScript). The PHP suite executes every SQL statement for real against SQLite rather than asserting on query strings — which is how it caught two non-portable constructs and a genuine bug in the tracking snippet.

The design decisions and their trade-offs are written up in [DECISIONS.md](https://github.com/Furnari-Marco/lms-wp-bridge/blob/main/DECISIONS.md).

### Also in production

Two further systems are being prepared for release as extracted core modules:

- **A technical SEO audit platform** — Python, Flask, Playwright. Crawls at scale, parses DOMs, reconciles third-party API data and produces client-facing reports. In use on real audits.
- **A headless CMS engine** — Next.js, file-based content, a code-free admin for non-technical clients. One engine, many sites: content, theme, blocks, translations and payments all editable by the client, behind a verification suite that has to pass before anything ships.

---

## Toolbox

`PHP` · `JavaScript` · `Python` · `Node.js` · `React` · `Next.js` · `WordPress` · `MySQL` · `REST APIs` · `Webhooks` · `SSO` · `Playwright` · `Linux` · `Nginx` · `Git`

---

## How I work

I don't consider something finished because it runs on my machine. Everything I own has a verification routine that runs before delivery — I would rather find the failure myself than have a client find it on a Monday morning. I write things down, including what was tried and rejected and why, because the next person to touch the code is usually me, a year later, having forgotten all of it.

Currently open to **Senior Solutions Engineer** and **Technical Account Manager** roles, remote across EMEA.

---

## Get in touch

The best way to reach me is **[LinkedIn](https://www.linkedin.com/in/marco-furnari-635545171/)**. Happy to talk about integration work, WordPress beyond the plugin directory, or anything in the repositories above.
