# b2bsearch: B2B people and company data as agent tools

<img src="assets/logo.png" width="64" height="64" alt="b2bsearch logo">

For Claude, Cursor and Grok Bot. Your agent counts a segment for free, then pulls the
rows it needs and pays per row through your Apify account.

| Tool | What it does |
|---|---|
| `people-database-search` | people by title, seniority, employer, size, industry, past employer, tenure; free counts and market breakdowns |
| `b2b-leads-finder` | people with a live email on every row; paste an Apollo search URL if you have one |
| `company-database-search` | 115M companies by country, industry, HQ, founding year, headcount, last funding round |
| `domain-to-decision-makers` | founders, C-level, VPs and directors at any domain, with the email that reaches them |
| `work-email-finder` | a work address from a name and a domain, with deliverability evidence |
| `linkedin-job-search-api` | 50M+ job postings as hiring signals; free preview with breakdowns |

Seven skills teach the agent the method: size first, cap the spend, keep lists clean,
report what was skipped. See [skills/](skills/).

## What the plugin connects to and sends

The plugin has no code of its own: no hooks, no local server, nothing that runs on your
machine. It adds one remote MCP server, Apify's hosted server at `mcp.apify.com` with six
b2bsearch Actors pre-selected, plus skills and commands that are plain text.

- You sign in to Apify in the browser (OAuth). The plugin never sees a token.
- What leaves your chat is the input of a tool call: search filters, company domains,
  names or profile links. It goes to Apify and to the b2bsearch Actors that run in your
  Apify account, which answer from the b2bsearch data service. Nothing else is sent.
- Results are stored as datasets in your Apify account, under its retention settings.

## Focused plugins

The same data, split by job. Each one is a separate repo with its own skills and a
smaller tool list, so the agent picks the right tool faster.

| Plugin | For |
|---|---|
| [Full ICP Search](https://github.com/keyvwin/full-icp-search) | size an ideal customer profile for free, then people, leads with emails and mobile numbers, decision makers, companies, job postings |
| [Contact Finder](https://github.com/keyvwin/contact-finder) | emails and phone numbers for people you already have, reverse email lookup, work email by name and domain, bulk CSV enrichment |
| [Phone Number Finder](https://github.com/keyvwin/phone-number-finder) | verified mobile numbers by profile URL, email or name and domain, call lists with a number and an email on every row, hiring companies to a call list |
| [B2B Leads Finder](https://github.com/keyvwin/b2b-leads-finder) | lead lists with emails and phones, saved-search import by URL, weekly top-ups without repeats |
| [Hiring Signals](https://github.com/keyvwin/hiring-signals) | who is hiring for a role, postings that mention a technology, decision makers at hiring companies |
| [Account Signals](https://github.com/keyvwin/account-signals) | new hires and job changes at target accounts, where former customer staff work now, lookalike companies |

In Claude Code all seven install from this marketplace:

```bash
claude plugin marketplace add keyvwin/b2bsearch-plugin
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


Generated from [recipes/tasks.json](https://github.com/keyvwin/b2bsearch-plugin/blob/main/recipes/tasks.json).
<!-- recipes:end -->

## Install

### Grok Bot

Once listed: **Settings → Plugins → b2bsearch → Connect**, sign in with Apify in the
browser window that opens. No API key to paste.

Today, before the listing, two ways:

- **Ready bots on the official Apify plugin.** Paste one file as the first message to a
  new bot, then add the Apify plugin (**Settings → Plugins → Apify → Add**):
  [Prospecting Desk](grok-bot/prospecting-desk.txt) (free market sizing, lead lists,
  decision makers, company lists), [Call List Desk](grok-bot/call-list-desk.txt) (verified
  mobile numbers from filters, from your own list, or from a hiring signal, with a call
  brief) and [Hiring Signals Watch](grok-bot/hiring-signals-watch.txt) (who is hiring,
  decision makers behind the hire, new senior hires, a Monday watch).
- **Custom MCP server.** Ask your bot to add it; the exact prompt is in
  [docs/grok-bot.md](docs/grok-bot.md).

### Cursor

One click, the MCP server only:

[![Add b2bsearch to Cursor](https://cursor.com/deeplink/mcp-install-dark.svg)](https://cursor.com/install-mcp?name=b2bsearch&config=eyJ1cmwiOiJodHRwczovL21jcC5hcGlmeS5jb20vP3Rvb2xzPWNhbGwtYWN0b3IsZmV0Y2gtYWN0b3ItZGV0YWlscyxiMmJzZWFyY2gvcGVvcGxlLWRhdGFiYXNlLXNlYXJjaCxiMmJzZWFyY2gvYjJiLWxlYWRzLWZpbmRlcixiMmJzZWFyY2gvY29tcGFueS1kYXRhYmFzZS1zZWFyY2gsYjJic2VhcmNoL2RvbWFpbi10by1kZWNpc2lvbi1tYWtlcnMsYjJic2VhcmNoL3dvcmstZW1haWwtZmluZGVyLGIyYnNlYXJjaC9saW5rZWRpbi1qb2Itc2VhcmNoLWFwaSZjbGllbnQ9YjJic2VhcmNoLXBsdWdpbiJ9)

With the skills: import this repository as a team marketplace
(**Dashboard → Plugins & MCPs → Add Marketplace → Import from Repo**), or copy the
folder to `~/.cursor/plugins/local/b2bsearch` and reload the window. Connect the
`b2bsearch` MCP server when Cursor asks; the browser opens the Apify sign-in.

### Claude

In Claude Code:

```bash
claude plugin marketplace add keyvwin/b2bsearch-plugin
claude plugin install b2bsearch@b2bsearch
```

Run `/mcp` to sign in to the `b2bsearch` server. You need an Apify account; the free plan
is enough to try every tool.

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
docs/grok-bot.md            connect today, without the listing
grok-bot/*.txt              setup messages for the three ready bots (Prospecting Desk, Call List Desk, Hiring Signals Watch)
```

MIT licence. Issues and requests: the GitHub issue tracker of this repository.
