# What makes a note-taking system compound instead of decay?

_Answered from the wiki on 2026-08-12._

## Answer

A collection compounds when adding to it makes the existing material **easier** to reach,
and decays when adding to it makes everything **harder** to find. Which one you get is
decided by whether the structure is a hierarchy or a graph.

A folder hierarchy forces one location per idea, and every idea worth keeping belongs in
several places at once. So each new item makes the tree slightly worse: more to scan, more
ambiguity about where a thing "should" live, and no new paths to anything that was already
there. A linked collection inverts this — adding a note adds edges as well as a node, so
existing material gains new routes in every time something lands nearby.

Two preconditions have to hold for that to actually work:

1. **The notes have to be specific enough to link precisely.** A note about one idea can be
   pointed at from anywhere and reused in any argument. A note about six things can't be
   pointed at precisely — there's no way to say "I mean the third paragraph" — so it never
   gets linked, and an unlinked note is a dead end you won't find again.
2. **The notes have to be understandable without you.** In eight months the reader has
   forgotten the context, the meeting, and why it mattered. A note that only makes sense to
   someone who already remembers the thing it's about can't be usefully linked to from
   anywhere else.

The failure mode on the other side is saving faster than you understand. Saving is cheap and
takes a second; understanding is expensive and takes attention. A system that makes saving
frictionless and understanding optional fills faster than it is digested, until searching it
costs more than re-finding the original source would have. The defence is to make the system
refuse to store what it hasn't digested — one idea per note, in your own words, under a title
stating a claim — plus distilling in layers separated by weeks, so that what you forget does
the filtering instead of you deciding on first read what mattered.

So the test for any system is simply: does it get more useful as it gets bigger, or less?

## Path taken through the graph

`wiki/INDEX.md` → **Linked Thought** (the compounding claim itself) → **The Collector's
Fallacy** (via its link, for the decay side) → **Atomic Notes** (precondition 1) → **Write
for the Stranger** (precondition 2) → **Progressive Summarization** (the counter-discipline
over time). **Zettelkasten** was read but added nothing the others didn't already carry.

## Citations

| Claim | Article | Underlying source |
|-------|---------|-------------------|
| Value is in the edges; linking compounds, filing decays | [Linked Thought](../wiki/Linked%20Thought.md) | `raw/notes/Why Second Brains Fail.md`, `raw/links/Zettelkasten.md` |
| Saving ≠ learning; the pile becomes a debt | [The Collector's Fallacy](../wiki/The%20Collector's%20Fallacy.md) | `raw/notes/Why Second Brains Fail.md`, `raw/transcripts/Second Pass - Ep 47 - Marisol Reyes.md` |
| One idea per note, titled as a claim | [Atomic Notes](../wiki/Atomic%20Notes.md) | `raw/notes/Why Second Brains Fail.md`, `raw/links/Zettelkasten.md`, `raw/transcripts/Second Pass - Ep 47 - Marisol Reyes.md` |
| Notes must stand up for a reader who wasn't there | [Write for the Stranger](../wiki/Write%20for%20the%20Stranger.md) | `raw/transcripts/Second Pass - Ep 47 - Marisol Reyes.md` |
| Distil in layers; forgetting is the filter | [Progressive Summarization](../wiki/Progressive%20Summarization.md) | `raw/transcripts/Second Pass - Ep 47 - Marisol Reyes.md` |
