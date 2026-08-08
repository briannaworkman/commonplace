# Second Brain — Operational Contract

Sources land in `raw/`. Claude compiles them into cross-linked articles in `wiki/`.
Obsidian renders the result as a graph. There is no database and no build step —
the markdown files *are* the system.

## Directories

| Path | What it holds |
|------|---------------|
| `raw/` | Sources, append-only. Never edit a source's body after it lands. The subfolder sets the type: `raw/notes/`, `raw/links/`. |
| `wiki/` | One article per concept, written by Claude. `wiki/INDEX.md` lists them all. |
| `outputs/` | Saved answers to questions. |

## The one rule that replaces a database

> A file in `raw/` has been ingested **if and only if** its path appears in the
> `sources:` list of some `wiki/` article.

That is the only record kept. To find un-ingested sources, list `raw/**/*.md` and
search `wiki/` for each path; anything with no match is new. Appending the path to
`sources:` *is* the act of recording it — so the memory can never drift out of sync
with the wiki, because there is only one copy of it.

## Naming — this one is load-bearing

**An article's filename is its title, in Title Case, with real spaces in the filename.**

```
✅ wiki/Atomic Notes.md          linked as [[Atomic Notes]]
✅ wiki/The Collector's Fallacy.md   linked as [[The Collector's Fallacy]]
❌ wiki/atomic-notes.md          kebab-case — [[Atomic Notes]] will NOT resolve
❌ wiki/atomic_notes.md          underscores — same problem
```

Do **not** slugify, kebab-case, lowercase, or strip spaces and punctuation from
filenames, even though that is the common convention elsewhere. Obsidian resolves
`[[Some Title]]` by looking for a file literally named `Some Title.md`. A kebab-case
filename means every link to it renders as a faded phantom node and the graph falls
apart — which defeats the entire point of the system.

The filename and the `title:` frontmatter field must be identical strings.

## Frontmatter

Raw sources:

```yaml
---
title: "…"
source_type: note        # note | link
source_url: "https://…"  # links only
captured: YYYY-MM-DD
---
```

Wiki articles:

```yaml
---
title: "…"
tags: [tag-one, tag-two]
updated: YYYY-MM-DD
sources:
  - raw/links/Example.md
related: ["[[Other Article]]"]
---
```

## Ingesting sources

1. Find un-ingested sources using the rule above. If there are none, say so and stop.
2. Read each source. If a `raw/links/` file contains only a bare URL, fetch the page
   and replace the body with the fetched text, keeping the frontmatter. If the fetch
   fails, leave the file alone, say so, and move on — it will be retried next time.
3. Add frontmatter to any source missing it. Never rewrite a source's body otherwise.
4. Read `wiki/INDEX.md` and map the ideas in the source to existing articles.
5. Create or update one article per concept. Articles are **evergreen explanations of
   an idea**, not summaries of a source — a reader should learn the concept without
   knowing where it came from. Add `[[wikilinks]]` in **both** directions: link the new
   article to related ones, and edit those to link back.
6. Append the source's path to the `sources:` list of every article you touched.
7. Add one line per new article to `wiki/INDEX.md`.
8. Report what changed: sources processed, articles created vs. updated, links added.

## Answering a question

Read `wiki/INDEX.md`, read the relevant articles, and follow `[[wikilinks]]` outward as
the question requires. Answer **only** from what the wiki says — if it does not cover
the question, say so plainly and name the source that would close the gap. Never fill a
gap from general knowledge without labelling it.

Save the answer to `outputs/YYYY-MM-DD-<slug>.md` with the question, the answer, the path
taken through the graph, and citations to both the articles and their `raw/` sources.
