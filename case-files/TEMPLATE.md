# Case file template

How to publish a new case file after an audit is delivered.

## Rules (non-negotiable)

1. **Never** include the domain name, business name, location, or anything identifying.
2. Industry type only ("dental practice", "law firm", "online store"). Keep it generic.
3. Every finding must trace to a real DNS lookup from the delivered audit. Never invent findings.
4. End every case file with the $39 Stripe order link CTA.
5. No em-dashes in copy. Use commas, periods, or hyphens.

## Steps

1. Copy `sample-dental-practice.html` to a new file named after the industry,
   e.g. `law-firm.html`. Use lowercase, hyphens, no spaces.
2. Delete the `.sample-banner` div entirely (samples only).
3. Rewrite: `<title>`, `h1`, `.meta` line, findings, "What was fixed", and the
   anonymity note stays as-is.
4. Update the `<title>` to `Case file: <industry> — Inboxproof` (no SAMPLE tag).
5. Add a `.case` block at the top of the list in `index.html` (newest first).
   Copy the existing block, change the link, headline, and summary. Remove the
   `sample` class from the pill, or drop the pill for real files.
6. Update `tally.json`: bump `audits_delivered` by 1, add the counts to
   `issues_found` and `critical_found`, set `updated` to today (YYYY-MM-DD).
7. Commit and push. GitHub Pages rebuilds automatically.

## Filename convention

`<industry-in-hyphens>.html` — e.g. `plumbing-company.html`, `real-estate-agency.html`.
If two case files share an industry, append a number: `dental-practice-2.html`.

## Finding block reference

Copy one of these per finding, changing the class and content:

```html
<div class="finding crit"><div class="tag">CRITICAL</div>
  <h4>Headline in plain English</h4>
  <p>What it means and why it matters.</p>
  <code>TXT &nbsp;name &nbsp; "record value"</code>
</div>
```

Classes: `crit` (red), `warn` (amber), `ok` (green). The `code` line is optional,
use it when there is an exact DNS record to show. Inside `code`, write the
record with `&nbsp;` separators as in the sample.

## Meta line format

```html
<p class="meta">Industry: &lt;industry&gt; &middot; Audit date: YYYY-MM &middot; Findings: N (X critical, Y warnings, Z passes)</p>
```

Use month precision only, never an exact date tied to a real customer.
