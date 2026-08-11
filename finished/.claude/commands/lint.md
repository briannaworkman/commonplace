---
description: Repair broken wikilinks, orphans, and duplicate articles
---

Run a maintenance pass over `wiki/`. Fix what is mechanical; report what needs a human.

## 1. Build the picture

Read every article. Collect every filename, every `title:`, and every `[[wikilink]]` target.

## 2. Broken links

A link whose text matches no filename. Usually one of two causes:

- **The filename is wrong** — it was slugified to `kebab-case`. Rename the file to its exact
  title in Title Case with spaces. This is the common one.
- **The article doesn't exist** — either fix the link text to point at the right article, or,
  if the concept genuinely deserves its own article, write a short stub and add it to
  `wiki/INDEX.md`.

Do not create a stub for every dangling link. A link to something that will never be an
article — a person's name, a passing product mention — should stop being a link and become
plain text.

## 3. Links split across lines

Search every article for a `[[` whose closing `]]` is on a later line. If the *target* (the
part before any `|`) contains the break, the link is dead — it resolves to nothing. Re-wrap
the line so the whole link sits together.

These are easy to miss because they are invisible in graph view whenever the same link also
appears in the article's `related:` list: the frontmatter copy resolves, so the connection
shows up and nothing looks faded. Fix them by reading, not by looking at the graph.

## 4. Orphans

Articles nothing links to. For each, find the most closely related article and link them —
in **both** directions. If an article has outbound links but no inbound ones, the fix is
usually to make one of its existing outbound links bidirectional rather than to invent a new
relationship.

Prefer linking from a *specific* article over a broad hub. Wiring everything to the biggest
hub makes that hub meaningless.

## 5. Near-duplicates

Two articles covering the same concept. Merge into the one with the better title: combine
their `sources:`, repoint every link, delete the loser, update `wiki/INDEX.md`.

## 6. Index and provenance

- `wiki/INDEX.md` has exactly one line per article, and no lines for articles that no longer
  exist.
- Every path in every `sources:` list is a file that exists.
- Every article's `title:` matches its filename exactly.

## 7. Contradictions

Two articles asserting incompatible things. **Do not silently pick a winner** — report both
with their sources and let a human decide.

## 8. Report

What you fixed, and what needs a decision.
