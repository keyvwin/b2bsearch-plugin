# You need companies, not people

## 25. Seed startups in Europe funded since 2025

[Task page](https://apify.com/b2bsearch/company-database-search/examples/seed-startups-europe-funded-since-2025) · `b2bsearch/company-database-search`

When: You need a list of companies, not people: by country, size and last funding round.

```json
{"countryGroups":["eu"],"hasFunding":true,"fundingRounds":["pre_seed","seed"],"fundedAfter":"2025-01-01","employeesMax":50,"maxResults":100}
```

Free step (preview): `b2bsearch/company-database-search` with

```json
{"countryGroups":["eu"],"hasFunding":true,"fundingRounds":["pre_seed","seed"],"fundedAfter":"2025-01-01","employeesMax":50,"previewOnly":true}
```

Free. On 2026-10-31: 1,650 companies.

Returns: Company cards: name, domain, headcount, industry, HQ and a funding block with the last round type and date.

Watch out: The eu group does not include the UK or Switzerland.

Next: Their founders: task 18 with the domains, or task 31 in one run.

Variant, [US Software Companies at Series A or B, 50–500 Employees](https://apify.com/b2bsearch/company-database-search/examples/us-series-a-b-software-companies) on `b2bsearch/company-database-search`:

```json
{"countries":["us"],"industries":["Software Development"],"employeesMin":50,"employeesMax":500,"hasFunding":true,"fundingRounds":["series_a","series_b"],"maxResults":100}
```

Variant, [Manufacturing Companies in Germany with 50–500 Employees](https://apify.com/b2bsearch/company-database-search/examples/manufacturing-companies-germany-50-500) on `b2bsearch/company-database-search`:

```json
{"countries":["de"],"industries":["Manufacturing"],"employeesMin":50,"employeesMax":500,"maxResults":100}
```

## 26. Companies like your best customers

[Task page](https://apify.com/b2bsearch/lookalike-company-finder/examples/companies-similar-to-your-best-customers) · `b2bsearch/lookalike-company-finder`

When: You know who buys and want more companies like them.

```json
{"seedDomains":["linear.app","posthog.com"],"maxPerSeed":25,"sameCountry":true,"sameSize":true}
```

Free step: No count: at most seeds times maxPerSeed companies; seeds with no match are free.

Returns: Company cards, each saying in matchedOn what it matched on (industry, country, size).

Watch out: Turn sameSize off to find bigger or smaller peers.

Next: Decision makers at the lookalikes: task 18.

## 27. Clean up a column of messy domains

[Task page](https://apify.com/b2bsearch/domain-to-company/examples/domain-to-company-name) · `b2bsearch/domain-to-company`

When: A spreadsheet column holds URLs and domains in every form and you need the company behind each.

```json
{"domains":["https://www.notion.so/product","asana.com","WWW.GONG.IO","linear.app/features","miro.com"]}
```

Free step: No count: at most the number of domains times the price per company found.

Returns: One company card per domain: name, LinkedIn page, headcount, industry, country, HQ.

Watch out: When two companies claim a domain the row says so and costs nothing instead of guessing.

Next: Decision makers: task 18 with the cleaned domains.

Source: [recipes/tasks.json](https://github.com/keyvwin/b2bsearch-plugin/blob/main/recipes/tasks.json).
