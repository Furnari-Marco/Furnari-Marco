# Marco Furnari

**I make platforms talk to each other.**

Eleven years in web operations, MarTech and API integrations. Most of it has been spent on the unglamorous seam between systems that were never designed to work together: a hosted LMS and a WordPress site, a CRM and a checkout, a marketing stack and a database that has to stay consistent at the end of the month.

I've been on both sides of that seam. I've built the integrations, and I've been the customer who had to live with them, running an online school, shipping client sites, and doing the technical SEO work that pays for none of it but breaks all of it. That has shaped how I work more than any framework has.

---

## What I do

- **Integrate platforms that don't share identity or data.** Webhooks, REST APIs, signed single sign-on, idempotent syncs, and the reconciliation you need for when a webhook silently doesn't arrive.
- **Work in WordPress at the level that matters.** Custom plugins, the REST API, `$wpdb`, cron, capabilities, and the security review that should come with all of it.
- **Automate what people are doing by hand.** Crawling, parsing, extraction, reporting, usually because someone was copying numbers into a spreadsheet every Monday.
- **Translate between engineering and the business.** Scoping what should *not* be built is the part of the job I'm best at, and the part clients thank me for a year later.

---

## Selected work

### [schema-driven-cms](https://github.com/Furnari-Marco/schema-driven-cms): the core of a CMS engine for client sites

Small businesses need a site they can edit without calling their developer and without being able to break it. This is the engine behind that: a site declares its shape once in a schema, and the admin forms, validation, storage, version history, translations and SEO output are all derived from that declaration. One engine, many sites.

What it demonstrates:

- **A content model that holds its shape.** One whitelist validator is the only way in: unknown keys dropped, types coerced, unsafe URLs and off-site images refused, documents bounded. It never throws. A client hitting Save on a bad form gets their field reverted, not a 500.
- **Decisions that came from operating it.** Version history that refuses to merge nearby edits, because the person undoing is thinking in actions. Redirects created automatically when a client renames a page. Nothing indexable until someone ticks the box. Colours emitted as RGB channels so a palette change needs no rebuild.
- **Translations that survive editing.** Stable keys derived from the schema, per-field fallback, and a deliberate refusal to machine-translate a client's legal text.
- **130 tests and a strict typecheck with no test framework and no build step.** `node --test` runs the TypeScript directly. The only dependencies are TypeScript and `@types/node`, both dev-only.

Its [DECISIONS.md](https://github.com/Furnari-Marco/schema-driven-cms/blob/main/DECISIONS.md) covers twenty of these trade-offs.

### [seo-audit-core](https://github.com/Furnari-Marco/seo-audit-core): the analysis core of a technical SEO platform

From parsed HTML to findings a client can act on: SEO extraction, technical issue detection, black-hat SEO detection and crawl-over-crawl comparison. Pure Python, with no network, database or framework, extracted from a platform in use on real audits.

What it demonstrates:

- **Treating false positives as the product risk.** An audit is worth paying for only if every line survives scrutiny; one wrong finding costs the credibility of the other forty. No finding rests on a single signal, and half the detection suite consists of ordinary markup (screen-reader labels, accordions, dropdowns, skip links, agency credits) that must produce nothing.
- **A CSS cascade resolver, because the rule that hides text is never in the style attribute.** Selector chains, specificity, `!important`, inheritance, and a deliberate refusal to evaluate what it cannot evaluate reliably, reporting "unknown" instead of guessing.
- **Judging a site against itself.** Keyword density and outbound link counts mean nothing in absolute terms; the site-wide pass computes the median across the crawl, so a directory site is not mistaken for a link scheme.
- **139 tests** against HTML fixtures, running in under a second with no network access.

### [lms-wordpress-bridge](https://github.com/Furnari-Marco/lms-wordpress-bridge): identity and entitlements across two platforms

A WordPress plugin that shares users and purchases with a hosted LMS. Enrollments and sales arrive over authenticated webhooks, learners cross into WordPress through signed single-use links, and membership checks are answered locally rather than by calling the platform.

What it demonstrates:

- **The parts that decide whether an integration survives production.** Staged webhook authentication, so a live feed can be secured without rejecting one delivery. Idempotent handlers, because webhook platforms re-deliver and the same event twice has to converge rather than duplicate. Unknown events acknowledged, because a 4xx makes the platform retry something this site will never understand.
- **A threat model written next to the code that answers it.** The signature covers the redirect target, tokens are single-use with a five minute life, and single sign-on refuses to authenticate any account that can edit or administer, so a leaked secret is worth a subscriber session and nothing more.
- **The risk the code cannot close, stated instead of faked.** An earlier mitigation was removed because it cost real learners access on mobile networks while barely inconveniencing an attacker.
- **A rollout runbook, and a dashboard built around silence.** The failure mode of this kind of integration is that deliveries stop and nobody notices until a customer cannot open what they paid for.
- **67 tests** over a WordPress stub and real SQL, with no PHPUnit and no external dependencies.

Its [DECISIONS.md](https://github.com/Furnari-Marco/lms-wordpress-bridge/blob/main/DECISIONS.md) covers twenty of these trade-offs, including two that came from bugs found in production.

---

## Toolbox

`WordPress` · `HTML` · `CSS` · `REST APIs` · `Webhooks` · `SSO` · `Technical SEO` · `Google Tag Manager` · `GA4` · `Hotjar` · `Marketing automation` · `Linux` · `DNS`

---

## How I work

I don't consider something finished because it runs on my machine. Everything I own has a verification routine that runs before delivery. I would rather find the failure myself than have a client find it on a Monday morning. I write things down, including what was tried and rejected and why, because the next person to touch the code is usually me, a year later, having forgotten all of it.

I build with AI assistants. I set the architecture, the requirements and the constraints, direct the implementation, and verify every piece before it ships. The code in these repositories was written that way; the design decisions are mine, and each repository explains them in its DECISIONS.md.

Currently open to **Senior Solutions Engineer** and **Technical Account Manager** roles, remote across EMEA.

---

## Get in touch

The best way to reach me is **[LinkedIn](https://www.linkedin.com/in/marco-furnari-635545171/)**. Happy to talk about integration work, WordPress beyond the plugin directory, or anything in the repositories above.
