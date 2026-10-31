---
name: hiring-to-calls
description: Chain from a hiring signal to a call list. Companies hiring for a role now, the decision makers who own the hire, then verified mobile numbers for them. Free preview first; each paid step states its maximum cost and waits for your yes, with a spend cap.
argument-hint: <role being hired, country, how many companies>
---

# Hiring companies to a call list

Request: $ARGUMENTS

If the request is empty, ask for the role being hired, the country and how many companies.

Every paid step below has its own price and its own yes.

1. **Preview, free.** `b2bsearch/hiring-companies-finder` with `previewOnly: true` (task
   20): employers and postings in the last month.
2. **Companies and the people behind the hire.** Run task 20 with `maxCompanies` and
   `decisionMakers: true`, with the decision-maker titles for that role (for sales:
   chief revenue, head of sales, vp sales). For other people at those companies, pass the
   company domains to `b2bsearch/domain-to-decision-makers` (task 18).
3. **Numbers.** `b2bsearch/linkedin-to-phone` with the decision makers' profile URLs
   (task 10). The most it can cost: people times the price per number found; people
   without a number are free.
4. **Report** one table: company, matching postings, person, title, email, mobile number.

## Tested inputs

{{task 20}}

{{task 18}}

{{task 10}}

{{rules}}
