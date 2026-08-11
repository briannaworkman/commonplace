# commonplace

Workshop materials — Claude Workshop Day, Detroit, 12 August 2026.

Drop a source into `raw/`, and Claude compiles it into cross-linked articles in `wiki/`.
Obsidian draws the graph. **No Python, no database, no build step** — a folder of markdown
files and a slash command you can read in a minute.

> A *commonplace book* is what readers kept for four centuries before software: a bound
> notebook of passages worth keeping, copied out by hand and cross-referenced so they could
> be found again. Milton kept one. So did Locke, who published his own system for indexing
> them. The practice is old and well-tested. What's new is that you no longer have to do the
> copying, the cross-referencing, or the indexing yourself.

---

## What's in here

| Folder | What it is |
|--------|-----------|
| **`starter/`** | The kit. Four sources waiting in `raw/` — a note, two links, and a podcast transcript — and an empty `wiki/`. **This is the one you open.** |
| **`finished/`** | The answer key — the same vault after one `/ingest`, plus reference versions of the commands you'll write. Compare against it, or just read it. |

If you fall behind during the session, don't scramble. `finished/` has the completed
version, and `starter/` works fine at your kitchen table afterwards.

---

## Before you start

1. **[Obsidian](https://obsidian.md/download)** — free, Mac/Windows/Linux.
2. **[Claude Code](https://claude.com/claude-code)** — signed in.

## Get the files

**No git needed:** green **Code** button above → **Download ZIP** → unzip. You'll get a
folder called **`commonplace-main`** — that's the repo root, and `starter/` is inside it.

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

Claude finds the four sources in `raw/`, reads them, fetches the one that's still a bare URL,
and writes articles into `wiki/` — one per concept, cross-linked in both directions, each recording
which source it came from.

Watch what happens to the transcript. It goes in full of timestamps, speaker labels, filler
and a tangent about coffee; it comes out as two clean articles. The raw file is never
touched — the mess stays archived, and only the understanding is extracted.

### 4. Look at the graph

Back to Obsidian. **Cmd/Ctrl + G**. Your notes are nodes; your `[[wikilinks]]` are edges.

You should get roughly **8 articles and 23 links**. Faded, hollow nodes would mean a broken
link — a filename that didn't match its title. Repairing those is what a `/lint` command
would do, and writing one is a good exercise after `/query`.

### 5. Look at what `/ingest` actually is — then write your own command

Open `.claude/commands/ingest.md`. It's a markdown file: a description, then numbered steps
in plain English. No code, nothing registered anywhere. **That's the whole mechanism.**

So write another one. `starter/README.md` walks you through building `/query` — the command
that asks your vault a question and answers only from what it actually read, with citations
back to the source.

Write the file by hand, or say **"help me write my own /query command"** and a skill in the
vault will ask you what you want out of it, then write the file from your answers. Either
way it ends up being *your* command — the interesting decisions (how far to follow links,
whether backlinks should count, what it does when it doesn't know) are yours to make.

That's the part worth taking home. Not this vault — the fact that you can hand a folder a
page of English and get a tool.

---

## Then make it yours

Drop your own source into `starter/raw/` and run `/ingest` again:

- **A note** — anything in your own words, into `raw/notes/`.
- **A link** — a file in `raw/links/` containing nothing but a URL. Claude fetches it,
  archives the text, and folds it in.
- **A transcript** — a podcast, meeting, or talk into `raw/transcripts/`. Messy is fine.

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

`starter/` ships exactly one, on purpose:

| Command | What it does | Where |
|---------|--------------|-------|
| `/ingest` | Compile new sources in `raw/` into `wiki/` articles | ships in `starter/` |
| `/query <question>` | Answer from the wiki, with citations, saved to `outputs/` | **you write this** |
| `/lint` | Repair broken links, orphans, and duplicate articles | a good third one |

They're plain markdown files in `.claude/commands/`. Adding a file adds a command — nothing
to register, nothing to restart. Reference versions of `/query` and `/lint` live in
`finished/` if you want to compare, but write yours first.

## And one skill

`.claude/skills/designing-commands/SKILL.md` — guidance for designing a command of your own.

The difference: **a command runs when you type its name; a skill sits there being findable.**
Claude notices a skill is relevant and reaches for it, so *"help me write my own /query
command"* is enough — you don't have to know it exists. Both are just markdown files in a
folder.
