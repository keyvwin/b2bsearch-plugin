# You have a list of companies

## 15. The leadership team of one company

[Task page](https://apify.com/b2bsearch/company-employees/examples/leadership-team-by-company-domain) · `b2bsearch/company-employees`

When: You research an account and need its C-level, VPs and directors.

```json
{"companies":["hubspot.com"],"roles":["cxo","vp","director"],"titleExcludes":["assistant","office of","executive operations","chief of staff"],"excludeLowSignal":true,"maxRows":200}
```

Free step (count): `b2bsearch/people-database-search` with

```json
{"mode":"count","companyDomains":["hubspot.com"],"seniority":["cxo","vp","director"]}
```

Free. Leads are the share of this count with a contact on record.

Returns: fullName, title, seniority, location, positionStartYear, hasWorkEmail, hasPersonalEmail and the profile link.

Watch out: Keep titleExcludes: executive assistants carry titles like "Office of the CEO".

Next: Emails for the people you pick: task 16 (contacts tier) or task 12.

## 16. Every employee, then contacts only where needed

[Task page](https://apify.com/b2bsearch/company-employees/examples/all-employees-by-company-domain) · `b2bsearch/company-employees`

When: You need a company's whole roster, and contacts only for some of it.

```json
{"companies":["stripe.com"],"profileDetail":"roster","maxRows":1000}
```

Free step (count): `b2bsearch/people-database-search` with

```json
{"mode":"count","companyDomains":["stripe.com"]}
```

Free. Leads are the share of this count with a contact on record.

Returns: Roster rows (light tier). The contacts task returns profiles with emails and phones and skips anyone without an address for free.

Watch out: profileDetail roster is the cheap tier; switch to contacts only for the people you will write to.

Next: Contacts for a shortlist only: the contacts task with mustHave email.

Variant, [Employee Emails and Phones at a Company by Domain](https://apify.com/b2bsearch/company-employees/examples/employee-emails-by-company-domain) on `b2bsearch/company-employees`:

```json
{"companies":["gong.io"],"roles":["director","vp","cxo"],"profileDetail":"contacts","mustHave":["email"],"maxRows":100}
```

## 17. Engineers at a company you recruit from

[Task page](https://apify.com/b2bsearch/company-employees/examples/engineers-at-a-company) · `b2bsearch/company-employees`

When: You recruit engineers from one company.

```json
{"companies":["datadoghq.com"],"titleContains":["engineer","developer"],"titleExcludes":["sales engineer","solutions engineer"],"excludeLowSignal":true,"maxRows":500}
```

Free step (count): `b2bsearch/people-database-search` with

```json
{"mode":"count","companyDomains":["datadoghq.com"],"titleKeywords":["engineer","developer"],"excludeTitleKeywords":["sales engineer","solutions engineer"]}
```

Free. Leads are the share of this count with a contact on record.

Returns: Roster rows with title, seniority, time in role and the profile link.

Watch out: titleExcludes drops sales engineers and solutions engineers.

Next: Personal emails for the shortlist: task 14.

## 18. The CEO and founders of a list of companies

[Task page](https://apify.com/b2bsearch/domain-to-decision-makers/examples/ceo-and-founders-by-company-domain) · `b2bsearch/domain-to-decision-makers`

When: You have target domains and need the person at the top of each, with an email.

```json
{"domains":["linear.app","vercel.com","supabase.com","posthog.com","retool.com"],"roles":["founder","cxo"],"maxPerCompany":3}
```

Free step: No count: at most domains times maxPerCompany people at the per-person price.

Returns: Rows ranked per company in _rank: title, seniority, profile link and an email that reaches the person today (company domain first, else personal, never a past employer).

Watch out: Every person delivered is charged, with or without an email; domains with nobody found are free.

Next: Mobile numbers for the ones worth a call: task 10 with the profile links.

Variant, [Marketing Decision Makers at a List of Companies](https://apify.com/b2bsearch/domain-to-decision-makers/examples/marketing-leaders-by-company-domain) on `b2bsearch/domain-to-decision-makers`:

```json
{"domains":["asana.com","miro.com","canva.com","calendly.com","loom.com"],"roles":["cxo","vp","director"],"titleKeywords":["marketing","growth","demand"],"maxPerCompany":3}
```

Variant, [CTOs and Engineering Leaders at a List of Companies](https://apify.com/b2bsearch/domain-to-decision-makers/examples/cto-and-engineering-leaders-by-domain) on `b2bsearch/domain-to-decision-makers`:

```json
{"domains":["netlify.com","sentry.io","grafana.com","clickup.com","airtable.com"],"roles":["cxo","vp","director"],"titleKeywords":["cto","chief technology officer","engineering"],"maxPerCompany":3}
```

## 19. The email format of a domain

[Task page](https://apify.com/b2bsearch/company-email-format-finder/examples/email-format-of-company-domains) · `b2bsearch/company-email-format-finder`

When: You have a name and a company and need to know how the company writes its addresses.

```json
{"domains":["stripe.com","n26.com","linear.app","hubspot.com","gong.io"],"sampleLimit":200}
```

Free step: No count: at most the number of domains times the price per confirmed domain.

Returns: pattern such as first.last, how many real addresses confirm it, how strongly they agree, and masked samples.

Watch out: Domains without evidence are free.

Next: The real address of a named person: work email by name and domain.

Source: [recipes/tasks.json](https://github.com/b2bsearch/b2bsearch-plugin/blob/main/recipes/tasks.json).
