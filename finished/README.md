# finished — the answer key

This is `starter/` after a single `/ingest`. Nothing else was done to it.

Open this folder as an Obsidian vault and press **Cmd/Ctrl + G** to see what your graph
should look like — or just read the articles here on GitHub.

## What one `/ingest` produced

Two sources in `raw/`:

- `raw/notes/Why Second Brains Fail.md` — a note, read as-is
- `raw/links/Zettelkasten.md` — started as a bare URL; Claude fetched the page and
  archived the text in place

Became four cross-linked articles:

| Article | The idea |
|---------|----------|
| [Zettelkasten](wiki/Zettelkasten.md) | Luhmann's slipbox — structure lives in the links, not a hierarchy |
| [Atomic Notes](<wiki/Atomic Notes.md>) | One idea per note, titled as a claim, so it can be linked precisely |
| [Linked Thought](<wiki/Linked Thought.md>) | The value is in the edges; linking compounds where filing decays |
| [The Collector's Fallacy](<wiki/The Collector's Fallacy.md>) | Mistaking having saved something for having learned it |

**4 articles, 11 links, 0 broken links, 0 orphans.**

## Things worth noticing

**Concepts, not summaries.** No article is "a summary of the note." Each explains one idea
on its own terms — you can read *Atomic Notes* without knowing where it came from. That's
what makes them reusable later.

**Links go both ways.** *Atomic Notes* links to *Linked Thought*, and *Linked Thought*
links back. Neither is subordinate to the other, so you can enter the graph anywhere.

**Ideas got split across sources.** *Atomic Notes* draws on both the note and the fetched
Wikipedia page — check its `sources:` list. Neither source alone contains that article.

**Every article carries its provenance.** The `sources:` field in each file's frontmatter
is what lets `/query` cite where an answer came from. It's also the system's entire memory
of what it has read — see `CLAUDE.md`.

## Your results will differ

Claude won't produce these four articles word for word, and might reasonably split the
concepts differently — five articles, or three. That's fine. Compare the *shape*: are the
articles about single ideas, do the links run both ways, does every article cite its
sources, and does the graph connect?

If your links render as faded hollow nodes, they're broken — a filename didn't match its
title. Run `/lint`.
