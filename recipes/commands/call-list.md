---
name: call-list
description: Build a cold calling list with verified mobile numbers. Either from filters (every lead with a mobile and a live email) or for people you already have as profile URLs, emails or "Name, domain" lines. Free count or a stated maximum first, then a capped run after your yes.
argument-hint: <who to call, or paste profile URLs / emails>
---

# Call list with mobile numbers

Request: $ARGUMENTS

If the request is empty, ask whether the user describes people to find or has a list.

## A. The user describes the people

`b2bsearch/b2b-leads-with-phones` (task 6): every row has a verified mobile number and a
live email.

1. Count free with `b2bsearch/people-database-search`, `mode: "count"`, the same filters
   (names in the table). About 1 in 5 US sales leaders has both a mobile and a live email
   (measured 2026-10-14); outside the US numbers are rare, so say so before running there.
2. Say the most 25 rows can cost (rows times the price per lead plus the price per
   number), wait for a yes, run with `maxResults: 25`, show rows.
3. Full run after a second yes, with `excludeDatasets` set to the sample's dataset id.

## B. The user has a list

`b2bsearch/linkedin-to-phone` (tasks 10 and 11): one entry per line in `profileUrls`,
profile URLs, emails and "Name, domain" lines mixed freely, up to 20,000 per run.

1. There is no count. Say the list length, that rows without a number are free, and the
   most the run can cost (list length times the price per number found). Wait for a yes.
2. Run, then report numbers found and the free `no_phone`, `not_found` and
   `profile_removed` rows.

`phone` is in E.164, ready for a dialer.

{{mapping}}

## Tested inputs

{{task 6}}

{{task 10}}

{{task 11}}

{{rules}}
