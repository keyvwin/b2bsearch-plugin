# You have an ICP and no list

## 1. Sales leaders at mid-size US companies

[Task page](https://apify.com/b2bsearch/b2b-leads-finder/examples/us-sales-leaders-with-emails) · `b2bsearch/b2b-leads-finder`

When: You sell to sales teams and need VPs and heads of sales and CROs with an email that reaches them.

```json
{"jobTitles":["vp sales","head of sales","chief revenue officer"],"countries":["us"],"companySizeMin":50,"companySizeMax":1000,"maxResults":100,"emailType":"any"}
```

Free step (count): `b2bsearch/people-database-search` with

```json
{"mode":"count","titleKeywords":["vp sales","head of sales","chief revenue officer"],"countries":["us"],"employeeCountMin":50,"employeeCountMax":1000}
```

Free. Leads are the share of this count with a contact on record.

Returns: One row per person: fullName, jobTitle, email with emailType work or personal, company name, domain, size and industry, location, profile URL, phoneOnRecord. People without a live email are skipped free and counted in a note row.

Watch out: maxPerCompany stops one big employer from filling the list.

Next: Mobile numbers for the best rows: task 10. More every week without repeats: excludeDatasets with the earlier run.

## 2. Small business owners

[Task page](https://apify.com/b2bsearch/b2b-leads-finder/examples/small-business-owners-us-with-emails) · `b2bsearch/b2b-leads-finder`

When: You sell to small businesses and need the owner, founder or CEO with an email.

```json
{"jobTitles":["owner","founder","ceo"],"excludeJobTitles":["product owner","process owner"],"countries":["us"],"companySizeMin":1,"companySizeMax":50,"emailType":"any","maxResults":100}
```

Free step (count): `b2bsearch/people-database-search` with

```json
{"mode":"count","titleKeywords":["owner","founder","ceo"],"excludeTitleKeywords":["product owner","process owner"],"countries":["us"],"employeeCountMin":1,"employeeCountMax":50}
```

Free. Leads are the share of this count with a contact on record.

Returns: Same rows as task 1, at companies of 1 to 50 people.

Watch out: "owner" also matches product owners and process owners: keep excludeJobTitles.

Next: Narrow to a state, city or industry with cities or industries; mobile numbers: task 6.

## 3. Managing directors in Germany

[Task page](https://apify.com/b2bsearch/b2b-leads-finder/examples/geschaeftsfuehrer-germany-with-emails) · `b2bsearch/b2b-leads-finder`

When: You sell to German SMEs and need the managing director.

```json
{"jobTitles":["geschäftsführer","inhaber","managing director","ceo"],"countries":["de"],"companySizeMin":10,"companySizeMax":250,"emailType":"any","maxResults":100}
```

Free step (count): `b2bsearch/people-database-search` with

```json
{"mode":"count","titleKeywords":["geschäftsführer","inhaber","managing director","ceo"],"countries":["de"],"employeeCountMin":10,"employeeCountMax":250}
```

Free. Leads are the share of this count with a contact on record.

Returns: Same rows as task 1, at German companies of 10 to 250 people.

Watch out: Local markets write titles in the local language: keep geschäftsführer and inhaber next to the English titles.

Next: Austria and Switzerland: countries at, ch (or countryGroups dach).

## 4. HR and talent leaders, or procurement managers

[Task page](https://apify.com/b2bsearch/b2b-leads-finder/examples/hr-and-talent-leaders-with-work-emails) · `b2bsearch/b2b-leads-finder`

When: You sell to a department (HR, people, talent acquisition, procurement) and need its leaders.

```json
{"jobTitles":["head of hr","hr director","hr manager","head of people","vp people","chief people officer","talent acquisition"],"seniority":["manager","director","vp","cxo"],"countries":["us"],"companySizeMin":200,"companySizeMax":2000,"emailType":"work","maxResults":100}
```

Free step (count): `b2bsearch/people-database-search` with

```json
{"mode":"count","titleKeywords":["head of hr","hr director","hr manager","head of people","vp people","chief people officer","talent acquisition"],"seniority":["manager","director","vp","cxo"],"countries":["us"],"employeeCountMin":200,"employeeCountMax":2000}
```

Free. Leads are the share of this count with a contact on record.

Returns: Same rows as task 1. With emailType work every address is at the person's current company.

Watch out: Keep the seniority floor (manager and up): titles alone bring specialists and interns. For procurement, search procurement, purchasing and sourcing, not supply chain.

Next: Leave out existing customers with excludeCompanyDomains.

Variant, [Procurement Managers at Manufacturing Companies with Emails](https://apify.com/b2bsearch/b2b-leads-finder/examples/procurement-managers-manufacturing-with-emails) on `b2bsearch/b2b-leads-finder`:

```json
{"jobTitles":["procurement","purchasing","sourcing"],"seniority":["manager","director","vp","cxo"],"industries":["Manufacturing"],"countries":["us"],"emailType":"any","maxResults":100}
```

## 5. Rerun a search built in Apollo

[Task page](https://apify.com/b2bsearch/b2b-leads-finder/examples/apollo-search-url-to-leads) · `b2bsearch/b2b-leads-finder`

When: You already built the people search in Apollo and want the same people with emails, without a seat or export credits.

```json
{"apolloUrl":"https://app.apollo.io/#/people?page=1&personTitles[]=founder&personTitles[]=ceo&personLocations[]=United%20States&organizationNumEmployeesRanges[]=11%2C20&organizationNumEmployeesRanges[]=21%2C50","emailType":"any","maxResults":100}
```

Free step: No free count for a pasted URL: run maxResults 25 first and check the rows.

Returns: Same rows as task 1, from the filters read out of the pasted URL.

Watch out: Paste the people-search results URL into apolloUrl; filters Apollo has and the database does not are reported in a note row.

Next: Weekly top-up of the same search with excludeDatasets.

## 6. People you can call, not just email

[Task page](https://apify.com/b2bsearch/b2b-leads-with-phones/examples/us-sales-leaders-mobile-numbers) · `b2bsearch/b2b-leads-with-phones`

When: You need a cold calling list: every row with a verified mobile number and a live email.

```json
{"jobTitles":["vp sales","head of sales"],"countries":["us"],"companySizeMin":50,"companySizeMax":1000,"maxResults":50}
```

Free step (count): `b2bsearch/people-database-search` with

```json
{"mode":"count","titleKeywords":["vp sales","head of sales"],"countries":["us"],"employeeCountMin":50,"employeeCountMax":1000}
```

Free. Leads are the share of this count with a contact on record.

Returns: phone in E.164, every number in phones, the email, title and company. A skipped_no_contact note row counts people without a mobile or an email; those are free.

Watch out: Numbers are US-centric: about 1 in 5 US sales leaders has both a mobile and a live email (measured 2026-10-14).

Next: Load the rows into a dialer; numbers for people you already have: task 10.

Variant, [Real Estate Agents and Brokers in the US with Mobile Numbers](https://apify.com/b2bsearch/b2b-leads-with-phones/examples/real-estate-agents-mobile-numbers) on `b2bsearch/b2b-leads-with-phones`:

```json
{"jobTitles":["realtor","real estate agent","real estate broker","broker associate"],"industries":["Real Estate"],"countries":["us"],"maxResults":50}
```

Source: [recipes/tasks.json](https://github.com/keyvwin/b2bsearch-plugin/blob/main/recipes/tasks.json).
