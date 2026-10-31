# You want a reason to reach out

## 20. Companies hiring account executives right now

[Task page](https://apify.com/b2bsearch/hiring-companies-finder/examples/companies-hiring-account-executives-us) · `b2bsearch/hiring-companies-finder`

When: You sell to teams that are growing: who is hiring for a role right now.

```json
{"jobTitles":["account executive"],"locations":["United States"],"postedLimit":"month","maxCompanies":25,"decisionMakers":true,"decisionMakerTitleKeywords":["chief revenue","chief sales","head of sales","vp sales","vice president of sales","vp of sales","sales director"],"decisionMakersPerCompany":2,"excludeAgencies":true}
```

Free step (preview): `b2bsearch/hiring-companies-finder` with

```json
{"jobTitles":["account executive"],"locations":["United States"],"postedLimit":"month","excludeAgencies":true,"previewOnly":true}
```

Free. On 2026-10-31: 3,344 employers with 12,279 matching postings in the last month.

Returns: One company row each with matchingJobs, job titles, jobs30d and jobs90d (hiring pace) and the company card; with decisionMakers on, the people who own the hire follow as rows of _type decision_maker.

Watch out: Keep excludeAgencies. Decision-maker titles are matched as written, so list them (chief revenue, head of sales, vp sales); a bare "sales" also matches Salesforce.

Next: Mobile numbers for the decision makers: task 10 with their profile links.

Variant, [Companies Hiring Software Engineers in Germany, with CTOs](https://apify.com/b2bsearch/hiring-companies-finder/examples/companies-hiring-engineers-germany-with-ctos) on `b2bsearch/hiring-companies-finder`:

```json
{"jobTitles":["software engineer","software developer"],"locations":["Germany"],"postedLimit":"month","maxCompanies":25,"decisionMakers":true,"decisionMakerRoles":["founder","cxo","vp"],"decisionMakerTitleKeywords":["cto","technology","engineering","founder"],"decisionMakersPerCompany":1,"excludeAgencies":true}
```

## 21. New senior hires at your target accounts

[Task page](https://apify.com/b2bsearch/new-hires-finder/examples/new-hires-at-target-accounts) · `b2bsearch/new-hires-finder`

When: New leaders pick vendors in their first months: who joined your target accounts.

```json
{"companyDomains":["hubspot.com","zendesk.com","asana.com","atlassian.com","monday.com"],"sinceMonths":12,"seniority":["director","vp","cxo"],"maxResults":100,"maxPerCompany":20}
```

Free step (count): `b2bsearch/people-database-search` with

```json
{"mode":"count","companyDomains":["hubspot.com","zendesk.com","asana.com","atlassian.com","monday.com"],"seniority":["director","vp","cxo"],"currentRoleStartedAfterDate":"2025-11"}
```

Free. Leads are the share of this count with a contact on record.

Returns: startedAt, the new title, previousCompany and previousTitle (the opening line of the email) and the profile link.

Watch out: Start dates are dense through 2025 and thinner for the most recent months, so look back 12 months.

Next: Emails for the new hires: task 12 with their profile links.

## 22. Former employees and where they are now

[Task page](https://apify.com/b2bsearch/former-employees-finder/examples/former-employees-of-a-company) · `b2bsearch/former-employees-finder`

When: Point it at a customer for champions who moved, at a competitor for people who already know the problem.

```json
{"companyDomains":["hubspot.com"],"previewOnly":false,"countries":["us"],"leftAfterYear":2024,"maxResults":100}
```

Free step (preview): `b2bsearch/former-employees-finder` with

```json
{"companyDomains":["hubspot.com"],"countries":["us"],"leftAfterYear":2024,"previewOnly":true}
```

Free count of the alumni.

Returns: currentCompany, currentTitle, currentRoleStartYear and the profile link of each former employee.

Watch out: leftAfterYear keeps it recent.

Next: Work emails at the new company: task 12, keep work_current.

## 23. New VPs of sales since last October

[Task page](https://apify.com/b2bsearch/people-database-search/examples/new-sales-leaders-since-october-2025) · `b2bsearch/people-database-search`

When: You want people who just started a role: new CFOs, new heads of people, new anything.

```json
{"mode":"people","countries":["us"],"titleKeywords":["vp sales","head of sales","vice president of sales"],"currentRoleStartedAfterDate":"2025-10","maxResults":100,"profileDetail":"row"}
```

Free step (count): `b2bsearch/people-database-search` with

```json
{"mode":"count","countries":["us"],"titleKeywords":["vp sales","head of sales","vice president of sales"],"currentRoleStartedAfterDate":"2025-10"}
```

Free. Leads are the share of this count with a contact on record.

Returns: People rows with title, employer and the start of the current role. On 2026-10-31: 5,870 US sales leaders started since October 2025.

Watch out: currentRoleStartedAfterDate takes a month, YYYY-MM.

Next: Emails: task 1 with the same titles.

## 24. Who hires for a technology in a city

[Task page](https://apify.com/b2bsearch/linkedin-job-search-api/examples/kubernetes-jobs-berlin-hiring-companies) · `b2bsearch/linkedin-job-search-api`

When: You sell to teams that use a technology: find it in the job descriptions.

```json
{"titleSearch":["devops engineer","platform engineer","site reliability engineer","cloud engineer"],"descriptionSearch":["kubernetes"],"locationSearch":["Berlin, Germany"],"timeRange":"30d","removeAgency":true,"limit":100}
```

Free step (preview): `b2bsearch/linkedin-job-search-api` with

```json
{"titleSearch":["devops engineer","platform engineer","site reliability engineer","cloud engineer"],"descriptionSearch":["kubernetes"],"locationSearch":["Berlin, Germany"],"timeRange":"30d","removeAgency":true,"previewOnly":true}
```

Free count of postings and employers.

Returns: Job rows with the employer card and the hiring signal; the free preview counts postings and employers.

Watch out: Write the city with its country ("Berlin, Germany"); a bare "Berlin" is refused. The description search reads at most 500 postings, so name titles and a city. Job data runs about 10 days behind: use 30 days, not 7.

Next: Decision makers at those employers: task 18 with their domains.

Source: [recipes/tasks.json](https://github.com/b2bsearch/b2bsearch-plugin/blob/main/recipes/tasks.json).
