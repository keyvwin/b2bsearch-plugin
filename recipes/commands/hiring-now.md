---
name: hiring-now
description: Find the companies hiring for a role right now, in a country or city, or the employers whose job postings mention a technology. Free preview of employers and postings first, then company rows with hiring pace and the decision makers behind the hire after your yes, with a spend cap.
argument-hint: <role, country or "City, Country", optional technology>
---

# Companies hiring now

Request: $ARGUMENTS

If the request is empty, ask for the role being hired and the country.

1. **A role in a country**: `b2bsearch/hiring-companies-finder` (task 20). Run the free
   preview first with `previewOnly: true`: employers and postings in the window.
2. **A technology or word in the job text**: `b2bsearch/linkedin-job-search-api` (task
   24), with `descriptionSearch`, a few titles and a city written with its country
   ("Berlin, Germany"). Free preview first with `previewOnly: true`.
3. Say the most the run can cost (`maxCompanies` times the price per employer, plus the
   decision makers times the price per person when `decisionMakers` is on), wait for a
   yes, run.
4. Report the employers by matching postings with their pace (`jobs30d`, `jobs90d`) and
   the people who own the hire. Next step: `/hiring-to-calls`.

Job data runs about 10 days behind: use a month (`postedLimit: "month"`, `timeRange:
"30d"`), not a week.

## Tested inputs

{{task 20}}

{{task 24}}

{{rules}}
