---
name: decision-makers
description: Find the decision makers at a list of companies by website domain, ranked per company (founder and CEO first, or the leaders of one function such as marketing, engineering or sales), with an email that reaches them today where one is on record. States the most the run can cost and runs after your yes, with a spend cap.
argument-hint: "<company domains, and which people: founders, CEO, marketing, engineering...>"
---

# Decision makers by company domain

Request: $ARGUMENTS

If the request is empty, ask for the company domains (or URLs) and which people: the
founders and CEO, or the leaders of a function.

1. Start from task 18, or its marketing or CTO variant. Set `roles` and `titleKeywords` to
   the function the user named; `maxPerCompany` 1 to 3.
2. There is no count. Every person delivered is charged, with or without an email; a
   domain with nobody found is a free row. The most the run can cost is domains times
   `maxPerCompany` times the price per person. Say it and wait for a yes.
3. Run `b2bsearch/domain-to-decision-makers`, up to 500 domains per run; full URLs are
   reduced to the domain.
4. Report per company in `_rank` order: name, title, `email` and `emailType` where on
   record, profile URL. Next step: mobile numbers for the people worth a call,
   `b2bsearch/linkedin-to-phone` with their profile URLs (task 10).

## Tested inputs

{{task 18}}

{{rules}}
