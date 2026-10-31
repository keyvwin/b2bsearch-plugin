---
name: b2b-count
description: Count a B2B segment for free before buying a single row. How many people match titles, seniority, countries, company size, industry or company domains, or how many people a pasted Sales Navigator search holds. Nothing is charged.
argument-hint: <titles, countries, company size, industry, or a Sales Navigator URL>
---

# Free segment count

Request: $ARGUMENTS

If the request is empty, ask who to count: titles or seniority, countries, company size,
industry, company domains.

1. A pasted Sales Navigator lead-search URL: run `b2bsearch/sales-navigator-search` with
   `{"salesNavigatorUrl": "<the URL>", "mode": "count"}`.
2. Anything else: run `b2bsearch/people-database-search` with `mode: "count"` and the
   filters, named as in the table below. Several markets or companies at once: one
   `segments` entry each, as in tasks 7 and 8. For the shape of the segment (countries,
   seniority, employer size, industries, top titles, top employers) run `mode: "market"`.
3. Give the number per segment. A count of 1,000,000 is the ceiling: narrow the filters.
   Offer the next step: `/leads` for people with emails, `/call-list` for mobile numbers.

Both modes are free, so no yes and no spend cap are needed for this command.

{{mapping}}

## Tested inputs

{{task 7}}

{{task 8}}

{{task 9}}

{{rules}}
