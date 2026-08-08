---
description: Repair broken wikilinks, stubs, and duplicates in the wiki
---

Run a maintenance pass over `wiki/`.

1. Read every article. Collect every `[[wikilink]]` target and every filename.
2. **Broken links** — a link whose text does not exactly match a filename. Fix by
   correcting the link text, or, if the concept genuinely deserves an article, create a
   short stub for it and add it to `wiki/INDEX.md`.
3. **Orphans** — articles nothing links to. Add a link from the most closely related
   article, in both directions.
4. **Near-duplicates** — two articles covering the same concept. Merge into the one with
   the better title, combine their `sources:`, repoint links, and delete the loser.
5. **Contradictions** — two articles asserting incompatible things. Do not silently pick
   a winner; report them.
6. Verify `wiki/INDEX.md` has exactly one line per article, and no lines for articles
   that no longer exist.

Report what you fixed and what needs a human decision.
