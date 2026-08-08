---
description: Compile new sources from raw/ into the wiki
---

Run the ingestion pipeline exactly as defined under "Ingesting sources" in `CLAUDE.md`.

1. **Find what's new.** List every `.md` file under `raw/`. For each path, search `wiki/`
   for that path appearing in a `sources:` list. Any path with no match is un-ingested.
   Report the list before you start work.
2. If nothing is un-ingested, say "Nothing to ingest" and stop.
3. Otherwise process each one per the contract: fetch bare-URL links, add missing
   frontmatter, map ideas onto existing articles, create or update one article per
   concept, and add `[[wikilinks]]` in both directions.
4. Append each source's path to the `sources:` of every article you touched, and add a
   line to `wiki/INDEX.md` for each new article.
5. Summarize: sources processed, articles created vs. updated, new links made, and any
   source you skipped because its fetch failed.

**Before you finish, check the naming rule** — it is the one thing that breaks the graph:
every article's filename must be its exact title in Title Case with spaces
(`wiki/Atomic Notes.md`, not `wiki/atomic-notes.md`). Do not slugify. Then confirm every
`[[link]]` you wrote points at a title that has a file. Report the article count and the
link count so it can be checked.
