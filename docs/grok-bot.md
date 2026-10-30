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

## A prospecting desk in one bot

[`grok-bot/prospecting-desk.txt`](../grok-bot/prospecting-desk.txt) turns a new bot into
the b2bsearch Prospecting Desk. It runs on the official Apify plugin, so it needs no
custom server:

1. Create a bot (**+ → Create a Bot**) and add the Apify plugin
   (**Settings → Plugins → Apify → Add**, approve the Apify sign-in).
2. Paste the file as the first message. The bot saves nine skills and two routines
   (off until you turn them on) and starts with a free count of your market.

Every paid run carries a spend cap, and nothing past the free count runs without a yes.

## What the marketplace listing changes

Nothing in the tools. The listing adds one-click **Connect** in Settings → Plugins, the
skills installed with the plugin, and visibility in the catalogue. The custom server
above keeps working either way.
