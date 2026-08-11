# starter — you're in the right place

This is the working vault. Open **this folder** (not the repo root) in both Obsidian and
Claude Code.

`raw/` has four sources waiting — a note, two links, and a podcast transcript. `wiki/` is
empty. That's the starting line.

---

## 1. Run the one command that ships

```
/ingest
```

Claude reads the four sources, fetches the two links, and writes cross-linked articles into
`wiki/`. Then press **Cmd/Ctrl + G** in Obsidian — you should get roughly **8 articles and
23 links** where a moment ago there was nothing.

---

## 2. Look at what `/ingest` actually is

Open `.claude/commands/ingest.md`.

It's a markdown file. Frontmatter with a description, then numbered steps in plain English.
No code. Nothing registered anywhere. **That is the entire mechanism** — a file in a folder.

Which means you can write another one.

---

## 3. Write `/query` yourself

Your vault can now answer questions, but nothing asks them. Build that.

Create **`.claude/commands/query.md`**. Two mechanics `/ingest` doesn't show you, because it
takes no argument:

```markdown
---
description: Answer a question from the wiki and save it to outputs/
argument-hint: <your question>
---
```

- `description` — shows up when you're picking a command.
- `argument-hint` — hints at what to type after `/query`.
- Somewhere in the body, write **`$ARGUMENTS`**. Whatever you type after `/query` gets
  substituted in there. Without it, your command never sees the question.

**What it should do** — the requirements, not the wording. That part's yours:

1. Read `wiki/INDEX.md`, pick the relevant articles, read them, and follow `[[wikilinks]]`
   outward as the question needs.
2. Answer **only** from what the wiki actually says. If the wiki doesn't cover it, say so
   plainly instead of guessing — and name what source would close the gap.
3. Save the answer to `outputs/YYYY-MM-DD-<slug>.md` with the question, the answer, the path
   it took through the graph, and citations to the articles **and** their `raw/` sources.
4. Report the answer inline.

**Two ways to do this, both legitimate:**

- **Write the file yourself.** Copy the shape from `ingest.md`. Fastest if you like typing.
- **Ask Claude to write it.** Paste the requirements above and say *"write this as
  `.claude/commands/query.md`."* Claude has already read `CLAUDE.md` and `ingest.md`, so it
  knows the house style. This is not cheating — bootstrapping your own tooling is the point.

Then run it:

```
/query What makes a note-taking system compound instead of decay?
```

Watch what it cites. It should point at specific articles *and* the raw sources beneath them.
Then try something your wiki definitely doesn't cover, and see whether it admits it.

> Stuck, or want to compare? `../finished/.claude/commands/query.md` is one way to write it.
> Try yours first — there's no single right answer, and yours will be shaped like your
> questions.

---

## 4. Then make it yours

Drop your own sources into `raw/` and run `/ingest` again:

- **A note** — anything in your own words, into `raw/notes/`.
- **A link** — a file in `raw/links/` containing nothing but a URL.
- **A transcript** — a podcast, meeting, or talk transcript into `raw/transcripts/`. Messy is
  fine; the noise gets stripped on the way into the article, not out of the archive.

And write more commands. `/lint` to repair broken links and orphans is a good next one —
there's a version in `../finished/` if you want a starting point. Or invent your own:
`/gaps` to list questions your wiki *can't* answer yet, `/weekly` to summarise what you
added, whatever fits how you actually work.

Run it a few times and the graph starts doing what folders never do: getting *more* useful as
it gets bigger.

---

## Files

```
CLAUDE.md            the contract Claude follows — read this one
.claude/commands/    /ingest lives here. Add files to add commands.
raw/notes/           your own notes
raw/links/           one URL per file
raw/transcripts/     podcasts, meetings, talks
wiki/                Claude's articles, one concept each
wiki/INDEX.md        the table of contents
outputs/             saved answers
```

Full instructions are in the [repo README](../README.md).
