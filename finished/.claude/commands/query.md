---
description: Answer a question from the wiki and save it to outputs/
argument-hint: <your question>
---

Answer a question against the knowledge base, following "Answering a question" in `CLAUDE.md`.

The question:

$ARGUMENTS

1. Read `wiki/INDEX.md`, pick the relevant articles, and read them — following
   `[[wikilinks]]` outward to neighbouring articles as the answer requires.
2. Synthesize a direct answer grounded **only** in the wiki. If the wiki does not cover
   the question, or covers it only partly, say so plainly rather than inventing an answer,
   and name what source would need ingesting to close the gap.
3. Write `outputs/YYYY-MM-DD-<slug>.md` containing the question, the answer, the path you
   took through the graph, and citations to the articles **and** their `raw/` sources.
4. Report the answer inline and link the saved file.
