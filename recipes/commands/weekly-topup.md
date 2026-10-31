---
name: weekly-topup
description: Add new leads to a list every week without repeats. Reruns the same search with every earlier dataset excluded, so nobody already delivered is delivered or charged again, keeps a small ledger of dataset ids in the project, and counts for free before paying.
argument-hint: <which search (filters, a saved input or a dataset id), how many new leads>
---

# Weekly top-up without repeats

Request: $ARGUMENTS

If the request is empty, ask which search to top up and how many new leads this week.

**Ledger.** Keep `leads/<search-name>.json` in the project: the Actor, the input without
`excludeDatasets`, every dataset id of that search with its date and rows delivered, and
the agreed weekly cap in rows and dollars. Create it on the first run.

1. **Count, free.** `b2bsearch/people-database-search` with `mode: "count"` and the same
   filters (names in the table). Subtract the rows already delivered. Too few left: say so
   and propose widening (another city, an adjacent title, a wider size band) before paying.
2. Say the most the run can cost (this week's number times the price per lead) and wait
   for a yes, unless it is inside the weekly cap the user agreed.
3. Run the same Actor and input with `excludeDatasets` set to every dataset id in the
   ledger and `maxResults` set to this week's number.
4. Add the new dataset id, the date and the rows to the ledger. Report new rows, skipped
   rows and why, the charge.

A fixed-input schedule in the Apify Console does not add new datasets to
`excludeDatasets`, so it would repeat people; let the agent run the top-up.

{{mapping}}

## Tested inputs

{{task 1}}

{{rules}}
