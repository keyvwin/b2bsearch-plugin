---
name: crm-bounce-check
description: Find the CRM contacts whose email will bounce because they changed jobs. Checks profile URLs against the email addresses on record and splits them into current-employer addresses, addresses from a past employer and nothing on record. States the most it can cost first and runs after your yes, with a spend cap.
argument-hint: <profile URLs of CRM contacts, a CSV column or a dataset id>
---

# CRM bounce check

Request: $ARGUMENTS

If the request is empty, ask for the profile URLs of the contacts (pasted, a CSV column or
a dataset id). Contacts with only an email: resolve them with `b2bsearch/email-to-linkedin`
first.

1. There is no count. Say the list length and the most the run can cost (list length
   times the price per email found; `work_other` rows cost less, profiles with nothing on
   record are free). Wait for a yes.
2. Run `b2bsearch/linkedin-email-finder` with `includePersonalEmails: false` (task 13), up
   to 1,000 profiles per run.
3. Read `emailType`. `work_current`: an address at today's employer. `work_other`: the
   CRM address most likely points at a former employer; fix it before the next sequence.
   Report the three counts and a table of the `work_other` contacts with the address now
   on record.
4. Next step: where those people work now, `b2bsearch/profile-lookup` with `compact: true`
   on their profile URLs (task 29).

## Tested inputs

{{task 13}}

{{task 29}}

{{rules}}
