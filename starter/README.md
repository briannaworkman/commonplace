# starter — you're in the right place

This is the working vault. Open **this folder** (not the repo root) in both Obsidian and
Claude Code.

`raw/` has three sources waiting. `wiki/` is empty. That's the starting line.

## Run it

```
/ingest
```

Claude reads the three sources, fetches the two links, and writes cross-linked articles
into `wiki/`. Then press **Cmd/Ctrl + G** in Obsidian to see the graph — you should get
roughly **6 articles and 15 links**.

Then ask it something:

```
/query What makes a note-taking system compound instead of decay?
```

## Then make it yours

- **A note** — anything in your own words, into `raw/notes/`.
- **A link** — a file in `raw/links/` containing nothing but a URL.

Run `/ingest` again. Repeat. The graph gets more useful as it grows, which is the whole
claim being tested.

## Files

```
CLAUDE.md            the contract Claude follows — read this one
.claude/commands/    /ingest, /query, /lint — plain markdown, edit them
raw/notes/           your own notes
raw/links/           one URL per file
wiki/                Claude's articles, one concept each
wiki/INDEX.md        the table of contents
outputs/             saved answers
```

Stuck, or want to compare? `../finished/` is this same vault after one `/ingest`.
Full instructions are in the [repo README](../README.md).
