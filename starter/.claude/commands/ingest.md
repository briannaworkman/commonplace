---
description: Compile new sources from raw/ into the wiki
---

Compile every un-ingested source in `raw/` into `wiki/` articles.

`CLAUDE.md` defines the frontmatter schemas, the naming rule, and what an article is. Follow
those. Everything below is the procedure.

## 1. Find what's new

List every `.md` file under `raw/`. For each path, search `wiki/` for that path appearing in
a `sources:` list. Any path with no match is un-ingested.

Report the list before doing any work. If nothing is un-ingested, say "Nothing to ingest"
and stop.

## 2. Read each source, according to its type

- **note** — read as-is.
- **link** — if the file contains only a bare URL, fetch the page and replace the body with
  the fetched text, keeping the frontmatter. If the fetch fails, leave the file alone, say
  so, and move on — the next run will retry it.
- **transcript** — read it, but **strip the noise on the way out**: speaker labels,
  timestamps, filler, crosstalk, tangents, and ad reads never appear in an article. Leave
  the file in `raw/` exactly as it is. The mess is the archive; the article is the
  understanding. Most of a transcript is not an idea — expect a long one to yield two or
  three articles, and do not pad to fill space.

Add frontmatter to any source missing it. Do not otherwise touch a source's body.

## 3. Map the ideas onto the existing wiki

Read `wiki/INDEX.md`. For each idea in the source, decide: does an article already cover
this? Prefer updating an existing article over creating a near-duplicate.

## 4. Write the articles

One article per concept. Add `[[wikilinks]]` in **both** directions — link the new article
to related ones, then edit those to link back.

## 5. Record provenance

Append the source's path to the `sources:` list of every article you touched. This is what
makes the source count as ingested, so it is not optional.

## 6. Update the index

Add one line per new article to `wiki/INDEX.md`.

## 7. Check your work before reporting

- Every article's filename is its exact title, Title Case, with spaces. **Do not slugify.**
- Every `[[link]]` you wrote points at a title that has a file.
- Every article you touched lists the source in `sources:`.

## 8. Report

Sources processed, articles created vs. updated, links added, and the final article and link
counts so they can be checked. Name any source you skipped and why.
