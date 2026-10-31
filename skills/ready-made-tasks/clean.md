# You have a mess to clean

## 28. Qualify inbound sign-ups by email

[Task page](https://apify.com/b2bsearch/reverse-email-lookup/examples/qualify-inbound-signups-by-email) · `b2bsearch/reverse-email-lookup`

When: You get sign-ups and need to know which is a VP at a real company and which is a student.

```json
{"emails":["jane.example@example.com","john.example@example.org","maria.example@example.net"],"compact":true}
```

Free step: No count: at most the number of emails times the price per person found; unmatched emails are free.

Returns: With compact on: the person, title, company, seniority and profile link per email.

Watch out: Personal Gmail addresses match too.

Next: The company card: task 27 with the employer's domain; the person who signs: task 18.

## 29. Where do your customer contacts work now

[Task page](https://apify.com/b2bsearch/profile-lookup/examples/where-do-my-contacts-work-now) · `b2bsearch/profile-lookup`

When: The people who signed your contracts may have moved: churn risk or a new account.

```json
{"profileUrls":["satyanadella","https://www.linkedin.com/in/reidhoffman"],"compact":true}
```

Free step: No count: at most the list length times the price per profile; not found is free.

Returns: With compact on: current title and company per profile URL. A changed companyName is the signal.

Watch out: Run it monthly on the same list.

Next: Emails at the new company: task 12.

## 30. A CRM export with a bit of everything

[Task page](https://apify.com/b2bsearch/waterfall-lead-enrichment/examples/crm-export-to-emails-and-phones) · `b2bsearch/waterfall-lead-enrichment`

When: Each row of the CSV carries a different key: an email, a profile URL, a name with a company, a domain.

```json
{"csv":"https://api.apify.com/v2/key-value-stores/3QjjLxhysmMUbUbyX/records/sample-waterfall.csv","contacts":true}
```

Free step: No count: at most the row count times the price per found row; misses are free.

Returns: Each row resolved by its strongest key to a profile (or a company for a bare domain), with contacts when contacts is on.

Watch out: csv takes a public URL of the file; up to 50,000 rows.

Next: People-only files: the bulk enrichment task.

Variant, [Enrich a CSV of Emails, Profile URLs and Names in Bulk](https://apify.com/b2bsearch/bulk-people-enrichment/examples/enrich-csv-of-emails-urls-and-names) on `b2bsearch/bulk-people-enrichment`:

```json
{"csv":"https://api.apify.com/v2/key-value-stores/3QjjLxhysmMUbUbyX/records/sample-people.csv","contacts":true}
```

Source: [recipes/tasks.json](https://github.com/b2bsearch/b2bsearch-plugin/blob/main/recipes/tasks.json).
