---
name: champion-moves
description: Find your champions who moved. Former employees of a customer (or a competitor) and where they work now, then their work email at the new company. Free alumni count first; each paid step states its maximum cost and waits for your yes, with a spend cap.
argument-hint: <customer or competitor domain, country, since which year>
---

# Champion moves

Request: $ARGUMENTS

If the request is empty, ask for the company domain, the country and since which year.

1. **Count, free.** `b2bsearch/former-employees-finder` with `previewOnly: true` (task
   22): how many alumni match.
2. **Alumni.** Say the most the run can cost (`maxResults` times the price per person),
   wait for a yes, run with `previewOnly: false` and `leftAfterYear`.
3. **Emails at the new company.** `b2bsearch/linkedin-email-finder` on their profile URLs
   (task 12). The most it can cost: people times the price per email found. After a yes,
   run and keep only `work_current` rows.
4. **Report**: person, old company, `currentCompany`, `currentTitle`, start year, email.

Contacts the user already tracks: `b2bsearch/profile-lookup` with `compact: true` on their
profile URLs (task 29) shows who moved.

## Tested inputs

{{task 22}}

{{task 12}}

{{task 29}}

{{rules}}
