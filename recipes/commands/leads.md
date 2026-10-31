---
name: leads
description: Build a B2B lead list where every row has a live email, from your ideal customer profile (titles, seniority, country, company size, industry, domains) or a pasted Apollo search URL. Free count first, a priced 25-lead sample, then the full list after your yes, with a spend cap.
argument-hint: <who, where, company size or industry, how many>
---

# Lead list with emails

Request: $ARGUMENTS

If the request is empty, ask: which titles or seniority, which countries or cities, what
company size or industry, how many leads.

1. **Start from a tested input.** Pick the closest task below and change only what the
   user asked. Keep its exclusions and its seniority floor.
2. **Count, free.** `b2bsearch/people-database-search` with `mode: "count"` and the same
   filters, named as in the table. Say: "N people match; leads are the share of them with
   a live email on record".
3. **Sample.** Say the most 25 leads can cost, wait for a yes, then run
   `b2bsearch/b2b-leads-finder` with `maxResults: 25`. Show five to ten rows. Wrong titles
   or companies: fix the filters and count again.
4. **Full list.** Say the most the full run can cost (`maxResults` times the price per
   lead), wait for a yes, run with `excludeDatasets` set to the sample's dataset id so
   nobody is paid for twice, and `maxPerCompany` when one employer must not fill the list.
5. **Report** and offer the next step: `/call-list` for mobile numbers, a weekly top-up
   for more next week without repeats.

A pasted Apollo people-search URL goes into `apolloUrl` (task 5): there is no free count
for it, so the 25-lead sample is the check. A pasted Sales Navigator URL: count it with
`/b2b-count`, then run `b2bsearch/sales-navigator-search` with `mode: "people"`.

{{mapping}}

## Tested inputs

{{task 1}}

{{task 2}}

{{task 3}}

{{task 4}}

{{task 5}}

{{rules}}
