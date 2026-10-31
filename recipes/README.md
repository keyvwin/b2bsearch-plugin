# Recipes

The source of the `ready-made-tasks` skill and the slash commands in all six b2bsearch
plugins. Edit here, then rebuild; never edit the generated files in the plugins.

- `tasks.json`: the jobs. Numbers 1 to 30 follow the article
  [30 ready-made B2B data tasks on Apify](https://dev.to/kevinhall/30-ready-made-b2b-data-tasks-on-apify-from-lead-lists-to-call-lists-4e21);
  31 and 32 came later. Each job has the public task page (`taskUrl`), the Actor, the
  tested `input` copied from that page, the free step (`count` on People Search,
  `preview` with `previewOnly`, `free` when the task is itself a count, `lookup` or
  `sample` when there is no count), what comes back, the trap to avoid and the next job.
  `plugins` says which jobs and commands each plugin gets.
- `commands/*.md`: command templates. `{{task N}}` expands to job N, `{{mapping}}` to the
  filter-name table, `{{rules}}` to the spend and safety rules every command shares.

```bash
# from this repository, with the plugin repositories cloned next to it
node scripts/build-recipes.mjs . ../full-icp-search ../b2b-leads-finder ../contact-finder ../hiring-signals ../account-signals
node scripts/build-recipes.mjs --check . ../full-icp-search ../b2b-leads-finder ../contact-finder ../hiring-signals ../account-signals
node scripts/build-recipes.mjs --links   # every task page answers 200
```

A job's input changes only when its task page changes: copy the new input from the page,
run the free step once, and update `checked`.
