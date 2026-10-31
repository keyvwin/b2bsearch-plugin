---
name: new-hires
description: Find new senior hires at your target accounts by company domain, with the start month, new title and the company and title they came from: a job change signal for outbound. Free count of the hires first, then the rows after your yes, with a spend cap.
argument-hint: <target account domains, levels, months back>
---

# New hires at target accounts

Request: $ARGUMENTS

If the request is empty, ask for the target account domains and which levels (director,
VP, C-level).

1. **Count, free.** `b2bsearch/people-database-search` with `mode: "count"`,
   `companyDomains`, `seniority` and `currentRoleStartedAfterDate` (`YYYY-MM`, 12 months
   back by default): that is the number of new hires.
2. Say the most the run can cost (`maxResults` times the price per person found;
   companies with no hires are free), wait for a yes, run `b2bsearch/new-hires-finder`
   with `sinceMonths`.
3. Report each hire with `startedAt`, the new title, `previousCompany` and
   `previousTitle`: the opening line of the email. Next step: work emails with
   `b2bsearch/linkedin-email-finder` on their profile URLs.

New leaders across a whole market instead of named accounts ("new VPs of sales in the
US"): task 23 on `b2bsearch/people-database-search`.

## Tested inputs

{{task 21}}

{{task 23}}

{{rules}}
