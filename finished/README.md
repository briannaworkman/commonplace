# finished — the answer key

This is `starter/` after a single `/ingest`. Nothing else was done to it.

It also carries **reference versions of the two commands you write yourself** —
`.claude/commands/query.md` and `.claude/commands/lint.md`. They're one way to write them,
not the only way. Try yours before reading these.

Open this folder as an Obsidian vault and press **Cmd/Ctrl + G** to see what your graph
should look like — or just read the articles here on GitHub.

## What one `/ingest` produced

Four sources in `raw/`:

| Source | Type | What happened |
|--------|------|---------------|
| `notes/Why Second Brains Fail.md` | note | Read as-is |
| `links/Zettelkasten.md` | link | Started as a bare URL; Claude fetched the page and archived the text in place |
| `links/Loops, Graphs, and When to Nest One Inside the Other.md` | link | Same — an essay on agent orchestration |
| `transcripts/Second Pass - Ep 47 - Marisol Reyes.md` | transcript | Read, noise stripped on the way out, file left untouched |

Became eight cross-linked articles:

| Article | The idea |
|---------|----------|
| [Zettelkasten](wiki/Zettelkasten.md) | Luhmann's slipbox — structure lives in the links, not a hierarchy |
| [Atomic Notes](<wiki/Atomic Notes.md>) | One idea per note, titled as a claim, so it can be linked precisely |
| [Linked Thought](<wiki/Linked Thought.md>) | The value is in the edges; linking compounds where filing decays |
| [The Collector's Fallacy](<wiki/The Collector's Fallacy.md>) | Mistaking having saved something for having learned it |
| [Progressive Summarization](<wiki/Progressive Summarization.md>) | Distil in layers separated by time; let forgetting filter |
| [Write for the Stranger](<wiki/Write for the Stranger.md>) | Your future self wasn't there either — notes must stand alone |
| [Loop Engineering](<wiki/Loop Engineering.md>) | One agent iterating until a checkable criterion is met |
| [Graph Engineering](<wiki/Graph Engineering.md>) | Run whatever isn't genuinely dependent in parallel |

**8 articles, 23 links, 0 broken links, 0 orphans.**

## Things worth noticing

**The transcript is the clearest demonstration.** Open
`raw/transcripts/Second Pass - Ep 47 - Marisol Reyes.md` next to
[Progressive Summarization](<wiki/Progressive Summarization.md>). The source has timestamps,
speaker labels, crosstalk, laughter, an interrupted thought, and a tangent about coffee
equipment. The article has none of that — just the idea, in clean prose, cited back to the
transcript. **The raw file was never edited.** The mess stays archived and only the
understanding is extracted, which is the difference between an archive and a summary: you
can always go back and check.

Note also that ~40 minutes of conversation produced two articles, not ten. Most of a
transcript is not an idea.

**Concepts, not summaries.** No article is "a summary of source X." Each explains one idea on
its own terms — you can read *Atomic Notes* without knowing where it came from.

**Links go both ways.** *Atomic Notes* links to *Write for the Stranger*, and it links back.
Neither is subordinate, so you can enter the graph anywhere.

**Ideas got split across sources.** *Atomic Notes* draws on the note, the Wikipedia page, and
the transcript — check its `sources:` list. No single source contains that article.

**Two unrelated sources turned out to agree.** A Wikipedia page about 1950s index cards and
an essay about orchestrating AI agents are not obviously about the same thing. But *Graph
Engineering*'s fake-edge test — does step B actually consume step A's output, or did you just
write them in that order? — is the same question *Linked Thought* asks about folders, which
impose one location on ideas that belong in several. Both say: keep the relationships that
are real, drop the ones your writing method invented.

Nobody planned that link. It appeared because both sources went into the same graph. That is
the entire argument for keeping one, and it's the thing a folder of PDFs will never do.

**`/query` was run too — see `outputs/`.** Two saved answers are in there. The first is a
normal one: an answer assembled from five articles, with the path it took through the graph
and citations down to the raw sources. The second is the one worth reading — a question the
wiki *doesn't* cover, where the honest answer is "this isn't in here," plus what to ingest to
close the gap. A system that will tell you it doesn't know is the one you can trust when it
says it does.

**Every article carries its provenance.** The `sources:` field is what lets `/query` cite
where an answer came from. It's also the system's entire memory of what it has read — see
`CLAUDE.md`.

## Your results will differ

Claude won't produce these eight articles word for word, and might reasonably split the
concepts differently — nine articles, or six. That's fine. Compare the *shape*: are the
articles about single ideas, do links run both ways, does every article cite its sources,
and does the graph connect?

If your links render as faded hollow nodes, they're broken — a filename didn't match its
title. Run `/lint`.

---

_The transcript is a sample: a fictional show and a fictional guest, written for this
workshop so the kit ships with something realistic to ingest. Swap in your own — a real
podcast, a meeting recording, a conference talk. Keep third-party transcripts in a private
repo; they belong to whoever made them._
