# One run for companies and people

## 31. Recently funded US startups with their founders

[Task page](https://apify.com/b2bsearch/full-icp-search/examples/recently-funded-us-startups-founders) · `b2bsearch/full-icp-search`

When: You want companies and the people to write to in one run: recently funded startups and their founders.

```json
{"find":"companies_and_people","previewOnly":false,"companyCountries":["us"],"fundingStages":["seed","series_a"],"fundedAfter":"2025-07-01","companySizeMin":11,"companySizeMax":200,"seniority":["founder"],"excludeJobTitles":["field cto","trainer","advisor","board"],"maxCompanies":25,"peoplePerCompany":2}
```

Free step (preview): `b2bsearch/full-icp-search` with

```json
{"find":"companies_and_people","companyCountries":["us"],"fundingStages":["seed","series_a"],"fundedAfter":"2025-07-01","companySizeMin":11,"companySizeMax":200,"seniority":["founder"],"previewOnly":true}
```

Free. On 2026-10-31: 1,102 companies.

Returns: A company row with round, amount and date, then up to two founders with an email that reaches them today.

Watch out: Keep seniority founder and the advisor and board exclusions. Funding rounds in the data run to late November 2025.

Next: Startups that are also hiring sellers: task 32.

## 32. Funded startups hiring their first sales reps

[Task page](https://apify.com/b2bsearch/full-icp-search/examples/funded-startups-hiring-first-sales-reps) · `b2bsearch/full-icp-search`

When: A seed or Series A startup posting its first AE or SDR jobs is building a sales team now.

```json
{"find":"companies_and_people","previewOnly":false,"companyCountries":["us"],"fundingStages":["seed","series_a"],"fundedAfter":"2025-07-01","companySizeMax":200,"hiringJobTitles":["account executive","sdr","sales development"],"seniority":["founder"],"excludeJobTitles":["advisor","board"],"maxCompanies":25,"peoplePerCompany":2,"jobsPerCompany":1}
```

Free step (preview): `b2bsearch/full-icp-search` with

```json
{"find":"companies_and_people","companyCountries":["us"],"fundingStages":["seed","series_a"],"fundedAfter":"2025-07-01","companySizeMax":200,"hiringJobTitles":["account executive","sdr","sales development"],"seniority":["founder"],"previewOnly":true}
```

Free. On 2026-10-31: 39 companies, 96 postings.

Returns: A company row with round and open jobs, up to two founders with an email, and one matching posting each.

Watch out: hiringJobTitles needs a country. Job data runs about 10 days behind.

Next: Mobile numbers for the founders: task 10.

Source: [recipes/tasks.json](https://github.com/b2bsearch/b2bsearch-plugin/blob/main/recipes/tasks.json).
