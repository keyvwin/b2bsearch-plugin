# b2bsearch for Grok Bot, Cursor and Claude Code

<img src="assets/logo.png" width="64" height="64" alt="b2bsearch logo">

B2B people and company data as agent tools. Your bot counts a segment for free, then
pulls the rows it needs and pays per row through your Apify account.

| Tool | What it does |
|---|---|
| `people-database-search` | people by title, seniority, employer, size, industry, past employer, tenure; free counts and market breakdowns |
| `b2b-leads-finder` | people with a live email on every row; paste an Apollo search URL if you have one |
| `company-database-search` | 115M companies by country, industry, HQ, founding year, headcount, last funding round |
| `domain-to-decision-makers` | founders, C-level, VPs and directors at any domain, with the email that reaches them |
| `work-email-finder` | a work address from a name and a domain, with deliverability evidence |
| `linkedin-job-search-api` | 50M+ job postings as hiring signals; free preview with breakdowns |
| `call-actor` | the other 29 [b2bsearch Actors](https://apify.com/b2bsearch) by id: company employees, new hires, lookalike companies, reverse email lookup, bulk enrichment, hiring companies |

Seven skills teach the agent the method: size first, cap the spend, keep lists clean,
report what was skipped. See [skills/](skills/).

## Focused plugins

The same data, split by job. Each one is a separate repo with its own skills and a
smaller tool list, so the agent picks the right tool faster.

| Plugin | For | Cursor Directory |
|---|---|---|
| [Full ICP Search](https://github.com/b2bsearch/full-icp-search) | size an ideal customer profile for free, then people, leads with emails and mobile numbers, decision makers, companies, job postings | [full-icp-search](https://cursor.directory/plugins/full-icp-search) |
| [Contact Finder](https://github.com/b2bsearch/contact-finder) | emails and phone numbers for people you already have, reverse email lookup, work email by name and domain, bulk CSV enrichment | [contact-finder](https://cursor.directory/plugins/contact-finder) |
| [B2B Leads Finder](https://github.com/b2bsearch/b2b-leads-finder) | lead lists with emails and phones, saved-search import by URL, weekly top-ups without repeats | [b2b-leads-finder](https://cursor.directory/plugins/b2b-leads-finder) |
| [Hiring Signals](https://github.com/b2bsearch/hiring-signals) | who is hiring for a role, postings that mention a technology, decision makers at hiring companies | [hiring-signals](https://cursor.directory/plugins/hiring-signals) |
| [Account Signals](https://github.com/b2bsearch/account-signals) | new hires and job changes at target accounts, where former customer staff work now, lookalike companies | [account-signals](https://cursor.directory/plugins/account-signals) |

In Claude Code all six install from this marketplace:

```bash
claude plugin marketplace add b2bsearch/b2bsearch-plugin
claude plugin install contact-finder@b2bsearch
```

Pricing is per row delivered, printed in each tool's description (people rows from
$0.95 per 1,000, leads with emails from $1.50 per 1,000, decision makers $3.20 per
1,000). Nothing is charged per search; counts and previews are free. On the Free Apify
plan each Actor gives an account 500 rows a month and up to 100 rows per run; the
people and leads searches return up to 25 rows per run when an agent starts them.
Any paid Apify plan lifts these limits.

<!-- recipes:start -->
## Commands and ready-made tasks

Type `/` in Cursor or Claude Code (Claude Code shows them with the plugin prefix, such as
`/b2bsearch:b2b-count`). Each command runs the free count or preview first, says the
most the run can cost, waits for your yes and then runs with a spend cap.

| Command | What it does |
|---|---|
| `/b2b-count` | Count a B2B segment for free before buying a single row. |
| `/leads` | Build a B2B lead list where every row has a live email, from your ideal customer profile (titles, seniority, country, company size, industry, domains) or a pasted Apollo search URL. |
| `/call-list` | Build a cold calling list with verified mobile numbers. |
| `/decision-makers` | Find the decision makers at a list of companies by website domain, ranked per company (founder and CEO first, or the leaders of one function such as marketing, engineering or sales), with an email that reaches them today where one is on record. |
| `/hiring-now` | Find the companies hiring for a role right now, in a country or city, or the employers whose job postings mention a technology. |
| `/new-hires` | Find new senior hires at your target accounts by company domain, with the start month, new title and the company and title they came from: a job change signal for outbound. |
| `/crm-bounce-check` | Find the CRM contacts whose email will bounce because they changed jobs. |
| `/hiring-to-calls` | Chain from a hiring signal to a call list. |
| `/weekly-topup` | Add new leads to a list every week without repeats. |
| `/champion-moves` | Find your champions who moved. |
| `/qualify-signup` | Qualify inbound sign-ups by email, Gmail included. |

The `ready-made-tasks` skill holds 32 tested inputs, each a public Apify task page:

- [1. Sales leaders at mid-size US companies](https://apify.com/b2bsearch/b2b-leads-finder/examples/us-sales-leaders-with-emails)
- [2. Small business owners](https://apify.com/b2bsearch/b2b-leads-finder/examples/small-business-owners-us-with-emails)
- [3. Managing directors in Germany](https://apify.com/b2bsearch/b2b-leads-finder/examples/geschaeftsfuehrer-germany-with-emails)
- [4. HR and talent leaders, or procurement managers](https://apify.com/b2bsearch/b2b-leads-finder/examples/hr-and-talent-leaders-with-work-emails)
- [5. Rerun a search built in Apollo](https://apify.com/b2bsearch/b2b-leads-finder/examples/apollo-search-url-to-leads)
- [6. People you can call, not just email](https://apify.com/b2bsearch/b2b-leads-with-phones/examples/us-sales-leaders-mobile-numbers)
- [7. How many software engineers per country](https://apify.com/b2bsearch/people-database-search/examples/software-engineers-by-country-free-count)
- [8. Compare sales team size across companies](https://apify.com/b2bsearch/people-database-search/examples/sales-team-size-by-company-free-count)
- [9. Count a Sales Navigator search before exporting it](https://apify.com/b2bsearch/sales-navigator-search/examples/count-sales-navigator-search-free)
- [10. Profile URLs to mobile numbers](https://apify.com/b2bsearch/linkedin-to-phone/examples/linkedin-urls-to-mobile-numbers)
- [11. CRM contacts with an email and no number](https://apify.com/b2bsearch/linkedin-to-phone/examples/crm-emails-to-mobile-numbers)
- [12. Profile URLs to work emails](https://apify.com/b2bsearch/linkedin-email-finder/examples/linkedin-urls-to-work-emails)
- [13. Find the CRM contacts who will bounce](https://apify.com/b2bsearch/linkedin-email-finder/examples/crm-contacts-with-past-employer-emails)
- [14. Personal emails for recruiting](https://apify.com/b2bsearch/linkedin-email-finder/examples/personal-emails-for-recruiting)
- [15. The leadership team of one company](https://apify.com/b2bsearch/company-employees/examples/leadership-team-by-company-domain)
- [16. Every employee, then contacts only where needed](https://apify.com/b2bsearch/company-employees/examples/all-employees-by-company-domain)
- [17. Engineers at a company you recruit from](https://apify.com/b2bsearch/company-employees/examples/engineers-at-a-company)
- [18. The CEO and founders of a list of companies](https://apify.com/b2bsearch/domain-to-decision-makers/examples/ceo-and-founders-by-company-domain)
- [19. The email format of a domain](https://apify.com/b2bsearch/company-email-format-finder/examples/email-format-of-company-domains)
- [20. Companies hiring account executives right now](https://apify.com/b2bsearch/hiring-companies-finder/examples/companies-hiring-account-executives-us)
- [21. New senior hires at your target accounts](https://apify.com/b2bsearch/new-hires-finder/examples/new-hires-at-target-accounts)
- [22. Former employees and where they are now](https://apify.com/b2bsearch/former-employees-finder/examples/former-employees-of-a-company)
- [23. New VPs of sales since last October](https://apify.com/b2bsearch/people-database-search/examples/new-sales-leaders-since-october-2025)
- [24. Who hires for a technology in a city](https://apify.com/b2bsearch/linkedin-job-search-api/examples/kubernetes-jobs-berlin-hiring-companies)
- [25. Seed startups in Europe funded since 2025](https://apify.com/b2bsearch/company-database-search/examples/seed-startups-europe-funded-since-2025)
- [26. Companies like your best customers](https://apify.com/b2bsearch/lookalike-company-finder/examples/companies-similar-to-your-best-customers)
- [27. Clean up a column of messy domains](https://apify.com/b2bsearch/domain-to-company/examples/domain-to-company-name)
- [28. Qualify inbound sign-ups by email](https://apify.com/b2bsearch/reverse-email-lookup/examples/qualify-inbound-signups-by-email)
- [29. Where do your customer contacts work now](https://apify.com/b2bsearch/profile-lookup/examples/where-do-my-contacts-work-now)
- [30. A CRM export with a bit of everything](https://apify.com/b2bsearch/waterfall-lead-enrichment/examples/crm-export-to-emails-and-phones)
- [31. Recently funded US startups with their founders](https://apify.com/b2bsearch/full-icp-search/examples/recently-funded-us-startups-founders)
- [32. Funded startups hiring their first sales reps](https://apify.com/b2bsearch/full-icp-search/examples/funded-startups-hiring-first-sales-reps)

Generated from [recipes/tasks.json](https://github.com/b2bsearch/b2bsearch-plugin/blob/main/recipes/tasks.json).
<!-- recipes:end -->

## Install

### Grok Bot

Once listed: **Settings → Plugins → b2bsearch → Connect**, sign in with Apify in the
browser window that opens. No API key to paste.

Today, before the listing, two ways:

- **Prospecting Desk template.** A ready bot on the official Apify plugin: free market
  sizing, lead lists, decision makers, hiring signals, weekly routines. Paste
  [grok-bot/prospecting-desk.txt](grok-bot/prospecting-desk.txt) as the first message to a
  new bot, then add the Apify plugin (**Settings → Plugins → Apify → Add**).
- **Custom MCP server.** Ask your bot to add it; the exact prompt is in
  [docs/grok-bot.md](docs/grok-bot.md).

### Cursor

One click, the MCP server only:

[![Add b2bsearch to Cursor](https://cursor.com/deeplink/mcp-install-dark.svg)](https://cursor.com/install-mcp?name=b2bsearch&config=eyJ1cmwiOiJodHRwczovL21jcC5hcGlmeS5jb20vP3Rvb2xzPWNhbGwtYWN0b3IsZmV0Y2gtYWN0b3ItZGV0YWlscyxiMmJzZWFyY2gvcGVvcGxlLWRhdGFiYXNlLXNlYXJjaCxiMmJzZWFyY2gvYjJiLWxlYWRzLWZpbmRlcixiMmJzZWFyY2gvY29tcGFueS1kYXRhYmFzZS1zZWFyY2gsYjJic2VhcmNoL2RvbWFpbi10by1kZWNpc2lvbi1tYWtlcnMsYjJic2VhcmNoL3dvcmstZW1haWwtZmluZGVyLGIyYnNlYXJjaC9saW5rZWRpbi1qb2Itc2VhcmNoLWFwaSZjbGllbnQ9YjJic2VhcmNoLXBsdWdpbiJ9)

With the skills: import this repository as a team marketplace
(**Dashboard → Plugins & MCPs → Add Marketplace → Import from Repo**), or copy the
folder to `~/.cursor/plugins/local/b2bsearch` and reload the window. Connect the
`b2bsearch` MCP server when Cursor asks; the browser opens the Apify sign-in.

### Claude Code

```bash
claude plugin marketplace add b2bsearch/b2bsearch-plugin
claude plugin install b2bsearch@b2bsearch
```

Run `/mcp` to sign in to the `b2bsearch` server.

### Any other MCP client

The server is Apify's hosted MCP with the b2bsearch tools pre-selected:

```
https://mcp.apify.com/?tools=call-actor,fetch-actor-details,b2bsearch/people-database-search,b2bsearch/b2b-leads-finder,b2bsearch/company-database-search,b2bsearch/domain-to-decision-makers,b2bsearch/work-email-finder,b2bsearch/linkedin-job-search-api
```

Streamable HTTP, OAuth 2.1 with dynamic client registration; an `Authorization:
Bearer <apify token>` header works where OAuth is not available.

## Try it

- "How many heads of sales work at Dutch companies with 50 to 500 employees?" (free)
- "Pull 50 of them with emails."
- "Who runs marketing at linear.app, vercel.com and supabase.com?"
- "Which US companies are hiring SDRs this month, and who is their VP of Sales?"

## Testing

Locally: point any MCP client at the server URL above, sign in, call
`b2bsearch--people-database-search` with `mode: "count"` and a title; a count comes back
in under ten seconds and costs nothing.

In-app: install the plugin, connect the MCP server, ask one of the prompts above.

## Data and rules

The data is a licensed professional-profile and company database; every row carries
the date its record was last refreshed. The plugin is for B2B research and
outbound. It is not for recruiting, consumer lists or looking up private individuals,
and the skills say so to the agent.

Apify terms and privacy apply to the account you connect:
[General terms](https://docs.apify.com/legal/general-terms-and-conditions) ·
[Privacy policy](https://docs.apify.com/legal/privacy-policy).

## Layout

```
plugin.json                 Agent Plugins 1.0.0 manifest
.cursor-plugin/plugin.json  Cursor plugin manifest
.claude-plugin/             Claude Code manifest and marketplace
mcp.json / .mcp.json        the hosted MCP server
skills/*/SKILL.md           seven skills (ready-made-tasks is generated)
commands/*.md               slash commands (generated)
recipes/                    tasks.json and the command templates: edit these
scripts/build-recipes.mjs   builds the skill, commands and README block of all six plugins
docs/grok-bot.md            connect today, without the listing
grok-bot/prospecting-desk.txt  setup message for the Prospecting Desk bot
```

MIT licence. Issues and requests: the GitHub issue tracker of this repository.
Actors and pricing: [apify.com/b2bsearch](https://apify.com/b2bsearch).
