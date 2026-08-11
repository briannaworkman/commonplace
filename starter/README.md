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

### The three things it has to do

Short list on purpose. Everything else is yours.

1. **Read the wiki before answering.** Start at `wiki/INDEX.md`.
2. **Answer only from what the wiki says.** If it's not in there, say so instead of guessing.
   This is the whole reason the thing is trustworthy.
3. **Cite what you used** — the articles, and the `raw/` sources beneath them.

### The decisions that are actually yours

This is where two people write genuinely different commands. There's no right answer to any
of these — pick, write it down, and see what you get.

**How far do you follow the links?** Only the articles the index summary suggests? Or do you
follow `[[wikilinks]]` one hop out from those? Two hops? A shallow command is fast and
focused. A deep one finds things you'd forgotten were connected — and sometimes wanders off.

**Do backlinks count for anything?** In Obsidian, open any article and look at its backlinks
panel — everything that points *at* it. An article with lots of inbound links is probably
load-bearing in your thinking; one with a single inbound link is probably a detail. Should
your command care? You could tell it to weight heavily-linked articles as more central, or to
follow backlinks as well as forward links, or to ignore direction entirely. Each gives you a
different answer to the same question.

**What happens at the edge of what you know?** Refuse flatly? Answer the part it can and mark
where the wiki stops? Name the specific source you'd need to ingest to close the gap? The
last one turns every unanswerable question into a reading list.

**Does it save every answer?** Always writing to `outputs/` builds a record of what you've
asked. Only saving on request keeps the folder clean. Your call.

**What should the answer look like?** Prose with links inline? A citations table? Should it
show you the *path* it took through the graph — which articles, in what order — or just the
conclusion? Seeing the path is how you catch it reading the wrong things.

**Two ways to do this, both legitimate:**

**A. Write the file yourself.** Copy the shape from `ingest.md`. Best if you already know
what you want and would rather just type it.

**B. Get walked through it.** Say this to Claude:

```
Help me write my own /query command
```

That triggers a skill in this vault — `.claude/skills/designing-commands/SKILL.md` — which
asks you the questions above as a single menu, then writes `.claude/commands/query.md` from
*your* answers. It also can't forget `$ARGUMENTS`, which is the mistake that silently breaks
a command.

Neither path is cheating. Bootstrapping your own tooling is the point.

> **A skill is the other kind of file.** A command runs when you type its name. A skill sits
> there being *findable* — Claude notices it's relevant and reaches for it, which is why
> "help me write my own /query command" was enough and you didn't have to know its name.
> Open `SKILL.md` afterwards. It's markdown, same as everything else.

Then run it:

```
/query What makes a note-taking system compound instead of decay?
```

Watch what it cites. It should point at specific articles *and* the raw sources beneath them.
Then try something your wiki definitely doesn't cover, and see whether it admits it.

> **Don't read `../finished/.claude/commands/query.md` yet.** It's there for when you're
> properly stuck, and it's one set of answers to the questions above — not the answers. If
> you read it first you'll write mine instead of yours, and mine is shaped like the questions
> *I* ask my notes. Yours should be shaped like the questions you ask.

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
