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

Six skills teach the agent the method: size first, cap the spend, keep lists clean,
report what was skipped. See [skills/](skills/).

Pricing is per row delivered, printed in each tool's description (people rows from
$0.95 per 1,000, leads with emails from $1.50 per 1,000, decision makers $3.20 per
1,000). Nothing is charged per search; counts and previews are free. The Free Apify
plan includes 500 rows a month.

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
skills/*/SKILL.md           six skills
docs/grok-bot.md            connect today, without the listing
grok-bot/prospecting-desk.txt  setup message for the Prospecting Desk bot
```

MIT licence. Issues and requests: the GitHub issue tracker of this repository.
Actors and pricing: [apify.com/b2bsearch](https://apify.com/b2bsearch).
