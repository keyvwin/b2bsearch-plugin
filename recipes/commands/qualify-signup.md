---
name: qualify-signup
description: Qualify inbound sign-ups by email, Gmail included. The person behind each address (name, title, seniority, company), the company card, and the decision maker who signs when the sign-up is not senior. States the most it can cost and runs after your yes, with a spend cap.
argument-hint: <one or more sign-up emails>
---

# Qualify a sign-up

Request: $ARGUMENTS

If the request is empty, ask for the sign-up emails.

1. **The person.** `b2bsearch/reverse-email-lookup` with `compact: true` (task 28).
   Unmatched emails are free; the most it can cost is the number of emails times the
   price per person found. Say it and wait for a yes.
2. **The company.** `b2bsearch/domain-to-company` with the employer's domain (task 27):
   headcount, industry, HQ, last funding round.
3. **The person who signs**, only when the sign-up is not senior:
   `b2bsearch/domain-to-decision-makers` on the domain with `roles` founder and cxo (or
   the function), `maxPerCompany: 2` (task 18). Price and yes first.
4. **Verdict** per sign-up: who, title, seniority, company size, and one line on fit:
   route to sales or not.

To run it on every new sign-up, call the same Actors from the sign-up webhook through the
Apify API, n8n, Make or Zapier.

## Tested inputs

{{task 28}}

{{task 27}}

{{task 18}}

{{rules}}
