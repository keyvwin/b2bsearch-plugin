# You hold profile URLs or emails

## 10. Profile URLs to mobile numbers

[Task page](https://apify.com/b2bsearch/linkedin-to-phone/examples/linkedin-urls-to-mobile-numbers) · `b2bsearch/linkedin-to-phone`

When: You have profile URLs (or emails, or names with a company) and need mobile numbers.

```json
{"profileUrls":["https://www.linkedin.com/in/jane-doe-example","https://www.linkedin.com/in/john-smith-example","https://www.linkedin.com/in/maria-garcia-example"]}
```

Free step: No count: the cost is at most the list length times the price per number found; misses are free.

Returns: A found row has primaryPhone, all numbers in phones, phoneCount, name, title, company and location. no_phone, not_found and profile_removed are free rows that say why.

Watch out: The field takes profile links, email addresses and "Name, domain" lines mixed in one list. Coverage is US-centric: about 1 in 4 US decision makers has a verified mobile on record.

Next: Emails for the same people: task 12.

## 11. CRM contacts with an email and no number

[Task page](https://apify.com/b2bsearch/linkedin-to-phone/examples/crm-emails-to-mobile-numbers) · `b2bsearch/linkedin-to-phone`

When: Your CRM has emails and no phone numbers.

```json
{"profileUrls":["jane.example@example.com","john.example@example.org","maria.example@example.net"]}
```

Free step: No count: at most the list length times the price per number found; misses are free.

Returns: Same rows as task 10, matched by email.

Watch out: Role mailboxes such as info@ or sales@ belong to no person and rarely match.

Next: Run 100 contacts first to see the rate for your list.

## 12. Profile URLs to work emails

[Task page](https://apify.com/b2bsearch/linkedin-email-finder/examples/linkedin-urls-to-work-emails) · `b2bsearch/linkedin-email-finder`

When: You have profile URLs and need the work email of each person.

```json
{"profileUrls":["https://www.linkedin.com/in/jane-doe-example","https://www.linkedin.com/in/john-smith-example","https://www.linkedin.com/in/maria-garcia-example"],"includePersonalEmails":false}
```

Free step: No count: at most the list length times the price per email found; profiles with nothing are free.

Returns: email, every company address on record in workEmails, and emailType: work_current is an address at today's employer, work_other one from somewhere else, usually an old job.

Watch out: Addresses come from the person's record, never from a first.last guess.

Next: Keep work_current for outreach; read work_other as task 13 does.

## 13. Find the CRM contacts who will bounce

[Task page](https://apify.com/b2bsearch/linkedin-email-finder/examples/crm-contacts-with-past-employer-emails) · `b2bsearch/linkedin-email-finder`

When: Your sequences bounce and you suspect contacts changed jobs.

```json
{"profileUrls":["https://www.linkedin.com/in/jane-doe-example","https://www.linkedin.com/in/john-smith-example","https://www.linkedin.com/in/maria-garcia-example"],"includePersonalEmails":false}
```

Free step: No count: at most the list length times the price per email found.

Returns: The same rows as task 12. Every work_other row is a contact whose CRM address probably points at a former employer.

Watch out: work_other rows cost less than work_current; profiles with nothing on record are free.

Next: Fix those before the next sequence; where they work now: task 29.

## 14. Personal emails for recruiting

[Task page](https://apify.com/b2bsearch/linkedin-email-finder/examples/personal-emails-for-recruiting) · `b2bsearch/linkedin-email-finder`

When: You recruit and should not write to a candidate at their work address.

```json
{"profileUrls":["https://www.linkedin.com/in/jane-doe-example","https://www.linkedin.com/in/john-smith-example","https://www.linkedin.com/in/maria-garcia-example"],"includePersonalEmails":true}
```

Free step: No count: at most the list length times the price per email found.

Returns: Same rows as task 12 plus gmail, outlook and other personal addresses.

Watch out: includePersonalEmails true is what adds the personal addresses.

Next: Candidates first: People Search with mode people (task 7).

Source: [recipes/tasks.json](https://github.com/keyvwin/b2bsearch-plugin/blob/main/recipes/tasks.json).
