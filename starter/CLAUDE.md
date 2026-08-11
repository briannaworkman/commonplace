# Second Brain — Operational Contract

Sources land in `raw/`. Claude compiles them into cross-linked articles in `wiki/`.
Obsidian renders the result as a graph. There is no database and no build step —
the markdown files *are* the system.

**This file holds only what is true all the time.** It is loaded into every session, so it
carries facts about the repo, not procedures. The procedures live in `.claude/commands/` —
one self-contained file per command, loaded only when that command actually runs.

## Directories

| Path | What it holds |
|------|---------------|
| `raw/` | Sources, append-only. Never edit a source's body after it lands. The subfolder sets the type: `raw/notes/`, `raw/links/`, `raw/transcripts/`. |
| `wiki/` | One article per concept, written by Claude. `wiki/INDEX.md` lists them all — one line each, either `[[Wikilink]]` or a markdown link, then an em dash, a one-line summary, and hashtags. |
| `outputs/` | Saved answers to questions. |

## The one rule that replaces a database

> A file in `raw/` has been ingested **if and only if** its path appears in the
> `sources:` list of some `wiki/` article.

That is the only record kept. To find un-ingested sources, list `raw/**/*.md` and search
`wiki/` for each path; anything with no match is new. Appending the path to `sources:` *is*
the act of recording it — so the memory can never drift out of sync with the wiki, because
there is only one copy of it.

## Naming — this one is load-bearing

**An article's filename is its title, in Title Case, with real spaces in the filename.**

```
✅ wiki/Atomic Notes.md              linked as [[Atomic Notes]]
✅ wiki/The Collector's Fallacy.md   linked as [[The Collector's Fallacy]]
❌ wiki/atomic-notes.md              kebab-case — [[Atomic Notes]] will NOT resolve
❌ wiki/atomic_notes.md              underscores — same problem
```

Do **not** slugify, kebab-case, lowercase, or strip spaces and punctuation from filenames,
even though that is the common convention elsewhere. Obsidian resolves `[[Some Title]]` by
looking for a file literally named `Some Title.md`. A kebab-case filename means every link
to it renders as a faded phantom node and the graph falls apart — which defeats the entire
point of the system.

The filename and the `title:` frontmatter field must be identical strings.

**Never let a line break fall inside `[[double brackets]]`.** Prose wraps; wikilinks must not.
A link whose target is split across two lines may not resolve, and it is invisible in the file
— it just quietly becomes a phantom node. If a link would push a line over, break the line
*before* the `[[` or *after* the `]]`, never inside.

## Frontmatter

Raw sources:

```yaml
---
title: "…"
source_type: note        # note | link | transcript
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

## What an article is

An **evergreen explanation of one idea** — not a summary of a source. A reader should learn
the concept without knowing where it came from. Two articles covering one idea is a bug; one
article covering three ideas is also a bug.

Links go in **both** directions. When you link a new article to an existing one, edit the
existing one to link back.

## Sources are append-only

Never edit a source's body once it has landed. Two exceptions, both at ingestion time: a
bare-URL link file gets its body replaced with the fetched page, and a source missing
frontmatter gets frontmatter added. Nothing else.

## Commands

One ships with this vault:

| Command | What it does |
|---------|--------------|
| `/ingest` | Compile new sources in `raw/` into `wiki/` articles |

It is a markdown file at `.claude/commands/ingest.md`. That is all a slash command is — a
file with a `description` and instructions in plain English. Adding another file to that
folder adds another command; there is nothing to register or restart.

**If asked to help write a new command**, use the `designing-commands` skill at
`.claude/skills/designing-commands/SKILL.md`. It exists so the person makes the design
decisions themselves rather than receiving a generic command. Follow it rather than
improvising, and write the command *file* — never do the command's job by hand instead.

That skill is itself just a markdown file. Same as everything else here.
