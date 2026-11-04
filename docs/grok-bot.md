# Connect b2bsearch to Grok Bot today

The plugin is submitted to the Grok Bot marketplace. Until it is listed, any Grok Bot
can use the same tools through a custom MCP server. Paste this to your bot:

```
Add a custom MCP server named b2bsearch. Transport: streamable HTTP. URL:
https://mcp.apify.com/?tools=call-actor,fetch-actor-details,b2bsearch/people-database-search,b2bsearch/b2b-leads-finder,b2bsearch/company-database-search,b2bsearch/domain-to-decision-makers,b2bsearch/work-email-finder,b2bsearch/linkedin-job-search-api
Authentication: OAuth, open the sign-in link for me. After it connects, call
b2bsearch--people-database-search with mode "count", titleKeywords ["head of sales"]
and countries ["nl"], and tell me the number. Counts are free.
```

The bot opens an Apify sign-in link; approve it with the Apify account that should pay
for rows (a free account is enough to start: 500 rows a month per Actor, up to 25 rows
per people or leads search). From then on the tools
appear in the bot's tool list and `@b2bsearch` is not needed, the bot picks them.

## Give the bot the method

The skills in this repository are what make the tools behave: count first, cap the
spend, label emails, skip the long tail unless asked. Grok Bot cannot install skills
from a repository yet, so paste the playbook into the bot's instructions:

1. Open the bot's settings, section **Instructions**.
2. Paste the contents of [`skills/prospecting-playbook/SKILL.md`](../skills/prospecting-playbook/SKILL.md)
   (the body below the frontmatter).
3. Add the specialised skills the bot will use most, for example
   `skills/people-search/SKILL.md` for list building or
   `skills/jobs-and-hiring-signals/SKILL.md` for hiring signals.

## Three ready bots, one file each

Each file in [`grok-bot/`](../grok-bot/) turns a new bot into a desk that runs on the
official Apify plugin, so it needs no custom server:

| File | Bot | What it does |
|---|---|---|
| `prospecting-desk.txt` | b2bsearch Prospecting Desk | free market sizing, people lists, leads with emails, decision makers by domain, company lists, hiring signals |
| `call-list-desk.txt` | b2bsearch Call List Desk | call lists with verified mobile numbers from filters, from a list you already have, or from a hiring signal; a call brief per row |
| `hiring-signals-watch.txt` | b2bsearch Hiring Signals Watch | who is hiring for a role or a technology, hiring pace, decision makers behind the hire, new senior hires, a Monday watch that reports only what is new |

1. Create a bot (**+ → Create a Bot**) and add the Apify plugin
   (**Settings → Plugins → Apify → Add**, approve the Apify sign-in).
2. Paste the file as the first message. The bot saves the skills and routines (routines
   stay off until you turn them on) and starts with a free count or preview.
3. To share it: bot name → **Share → Create a copy → Publish → Copy link**. The link
   carries the skills, routines and the Apify plugin; the recipient signs in to Apify once.

Every paid run carries a spend cap, and nothing past the free count runs without a yes.

## What the marketplace listing changes

Nothing in the tools. The listing adds one-click **Connect** in Settings → Plugins, the
skills installed with the plugin, and visibility in the catalogue. The custom server
above keeps working either way.
