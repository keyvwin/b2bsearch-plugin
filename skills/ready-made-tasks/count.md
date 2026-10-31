# Count before you pay for a single row

## 7. How many software engineers per country

[Task page](https://apify.com/b2bsearch/people-database-search/examples/software-engineers-by-country-free-count) · `b2bsearch/people-database-search`

When: You need the size of a market before you buy a list.

```json
{"mode":"count","titleKeywords":["software engineer","software developer"],"segments":[{"name":"United States","countries":["us"]},{"name":"India","countries":["in"]},{"name":"United Kingdom","countries":["gb"]},{"name":"Germany","countries":["de"]},{"name":"Canada","countries":["ca"]}]}
```

Free step: The task itself is a free count.

Returns: One row per segment with _total. On 2026-10-31: UK 185,825, Canada 166,391, Germany 116,071; the US and India stop at the 1,000,000 ceiling.

Watch out: A count at the 1,000,000 ceiling means narrow before you pull.

Next: Rows: switch mode to people. Lists with emails: task 1.

Variant, [Find Professionals Between Jobs: Open-to-Work Talent](https://apify.com/b2bsearch/people-database-search/examples/professionals-between-jobs) on `b2bsearch/people-database-search`:

```json
{"mode":"people","countries":["us"],"onlyBetweenJobs":true,"pastTitleKeywords":["product manager"],"maxResults":100,"profileDetail":"row"}
```

Variant, [Early-Career Software Engineers Who Started After 2020](https://apify.com/b2bsearch/people-database-search/examples/early-career-software-engineers) on `b2bsearch/people-database-search`:

```json
{"mode":"people","countries":["us"],"titleKeywords":["software engineer"],"careerStartYearMin":2021,"maxResults":100,"profileDetail":"row"}
```

## 8. Compare sales team size across companies

[Task page](https://apify.com/b2bsearch/people-database-search/examples/sales-team-size-by-company-free-count) · `b2bsearch/people-database-search`

When: You size a territory or need a competitor slide: how many salespeople each company has.

```json
{"mode":"count","titleKeywords":["account executive","sales development","business development","sales manager"],"segments":[{"name":"Salesforce","companyDomains":["salesforce.com"]},{"name":"HubSpot","companyDomains":["hubspot.com"]},{"name":"Zendesk","companyDomains":["zendesk.com"]},{"name":"Freshworks","companyDomains":["freshworks.com"]},{"name":"Gong","companyDomains":["gong.io"]}]}
```

Free step: The task itself is a free count.

Returns: One row per company domain with _total. On 2026-10-31: Salesforce 20,484, HubSpot 3,022, Zendesk 1,456.

Next: The people themselves with emails: task 1 with companyDomains.

## 9. Count a Sales Navigator search before exporting it

[Task page](https://apify.com/b2bsearch/sales-navigator-search/examples/count-sales-navigator-search-free) · `b2bsearch/sales-navigator-search`

When: You built a lead search in Sales Navigator and want the people without a seat or cookies.

```json
{"salesNavigatorUrl":"https://www.linkedin.com/sales/search/people?query=(recentSearchParam%3A(doLogHistory%3Atrue)%2Cfilters%3AList((type%3ACURRENT_TITLE%2Cvalues%3AList((text%3AHead%2520of%2520Growth%2CselectionType%3AINCLUDED)))%2C(type%3AREGION%2Cvalues%3AList((id%3A103644278%2Ctext%3AUnited%2520States%2CselectionType%3AINCLUDED)))%2C(type%3ACOMPANY_HEADCOUNT%2Cvalues%3AList((id%3AD%2Ctext%3A51-200%2CselectionType%3AINCLUDED)%2C(id%3AE%2Ctext%3A201-500%2CselectionType%3AINCLUDED)))))","mode":"count"}
```

Free step: The task itself is a free count (mode count).

Returns: The count of matching people (the sample US heads of growth search: 1,278). The export task returns the people as rows.

Watch out: Paste the lead-search URL as it is in the address bar.

Next: Export with the same URL; emails and phones with profileDetail contacts.

Variant, [Export a Sales Navigator Search: US Heads of Growth](https://apify.com/b2bsearch/sales-navigator-search/examples/head-of-growth-us-export) on `b2bsearch/sales-navigator-search`:

```json
{"salesNavigatorUrl":"https://www.linkedin.com/sales/search/people?query=(recentSearchParam%3A(doLogHistory%3Atrue)%2Cfilters%3AList((type%3ACURRENT_TITLE%2Cvalues%3AList((text%3AHead%2520of%2520Growth%2CselectionType%3AINCLUDED)))%2C(type%3AREGION%2Cvalues%3AList((id%3A103644278%2Ctext%3AUnited%2520States%2CselectionType%3AINCLUDED)))%2C(type%3ACOMPANY_HEADCOUNT%2Cvalues%3AList((id%3AD%2Ctext%3A51-200%2CselectionType%3AINCLUDED)%2C(id%3AE%2Ctext%3A201-500%2CselectionType%3AINCLUDED)))))","mode":"people","maxResults":100,"profileDetail":"row"}
```

Source: [recipes/tasks.json](https://github.com/keyvwin/b2bsearch-plugin/blob/main/recipes/tasks.json).
