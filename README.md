# commonplace

Workshop materials — Claude Workshop Day, Detroit, 12 August 2026.

Drop a source into `raw/`, and Claude compiles it into cross-linked articles in `wiki/`.
Obsidian draws the graph. **No Python, no database, no build step** — markdown files and
three slash commands.

> A *commonplace book* is what readers kept for four centuries before software: a bound
> notebook of passages worth keeping, copied out by hand and cross-referenced so they could
> be found again. Milton kept one. So did Locke, who published his own system for indexing
> them. The practice is old and well-tested. What's new is that you no longer have to do the
> copying, the cross-referencing, or the indexing yourself.

---

## What's in here

| Folder | What it is |
|--------|-----------|
| **`starter/`** | The kit. Two sources waiting in `raw/`, an empty `wiki/`. **This is the one you open.** |
| **`finished/`** | The answer key — the same kit after one `/ingest`. Four articles, eleven links. Compare against it, or just read it. |

If you fall behind during the session, don't scramble. `finished/` has the completed
version, and `starter/` works fine at your kitchen table afterwards.

---

## Before you start

1. **[Obsidian](https://obsidian.md/download)** — free, Mac/Windows/Linux.
2. **[Claude Code](https://claude.com/claude-code)** — signed in.

## Get the files

**No git needed:** green **Code** button above → **Download ZIP** → unzip.

**Or clone:**

```bash
git clone https://github.com/briannaworkman/commonplace.git
```

---

## The five steps

> **Open `starter/` — not the folder you downloaded.** The repo root holds two vaults;
> `starter/` is the one you work in. Both Obsidian and Claude Code should point there.

### 1. Open `starter/` in Obsidian

Obsidian → **Open folder as vault** → select the **`starter`** folder. Trust it when asked.
You'll see `raw/` and `wiki/`. Press **Cmd/Ctrl + G** for graph view — it's empty. That's
the starting line.

### 2. Open the same `starter/` folder in Claude Code

It reads `CLAUDE.md` on its own. That file is the entire system, and it's about a page long.
Worth reading while things load.

### 3. Ingest

```
/ingest
```

Claude finds the two sources in `raw/`, reads them, fetches the link, and writes articles
into `wiki/` — one per concept, cross-linked in both directions, each recording which source
it came from.

### 4. Look at the graph

Back to Obsidian. **Cmd/Ctrl + G**. Your notes are nodes; your `[[wikilinks]]` are edges.

You should get **4 articles and 11 links**. Faded, hollow nodes would mean a broken link —
run `/lint` if you see any.

### 5. Ask it something

```
/query What makes a note-taking system compound instead of decay?
```

Claude reads the index, walks the graph, and answers **only** from what your wiki actually
says — citing the articles and the raw sources beneath them. If the wiki doesn't cover it,
it tells you instead of guessing. The answer saves to `outputs/`.

---

## Then make it yours

Drop your own source into `starter/raw/` and run `/ingest` again:

- **A note** — anything in your own words, into `raw/notes/`.
- **A link** — a file in `raw/links/` containing nothing but a URL. Claude fetches it,
  archives the text, and folds it in.

Run it a few times and the collection starts doing what folders never do: getting *more*
useful as it gets bigger.

---

## How it remembers what it's read

There's no database. One rule, from `CLAUDE.md`:

> A file in `raw/` has been ingested **if and only if** its path appears in the `sources:`
> list of some `wiki/` article.

The wiki's own citations *are* the memory. Nothing to sync, nothing to corrupt, and you can
audit it by reading it.

## The commands

| Command | What it does |
|---------|--------------|
| `/ingest` | Compile new sources in `raw/` into `wiki/` articles |
| `/query <question>` | Answer from the wiki, with citations, saved to `outputs/` |
| `/lint` | Repair broken links, orphans, and duplicate articles |

They live in `.claude/commands/` as plain markdown. Edit them — that's the point.
