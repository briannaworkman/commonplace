---
description: Answer a question from the wiki and save it to outputs/
argument-hint: <your question>
---

Answer this question using only the knowledge base:

$ARGUMENTS

## 1. Walk the graph

Read `wiki/INDEX.md` and pick the articles that look relevant. Read them. Follow their
`[[wikilinks]]` outward to neighbouring articles as the question requires — the answer often
sits in an article the index summary didn't obviously point at.

Keep track of the order you read things in. That path is part of the output.

## 2. Answer only from what the wiki says

Ground every claim in an article you actually read.

If the wiki doesn't cover the question, **say so plainly** and name the source that would
close the gap. If it covers the question only partly, answer the part it covers and mark the
boundary. Never fill a gap from general knowledge without labelling it as outside the wiki —
a system that admits what it doesn't know is the only kind you can trust when it says it
does.

## 3. Save it

Write `outputs/YYYY-MM-DD-<slug>.md` containing:

- the question
- the answer
- **the path taken through the graph** — which articles you read, in order
- **citations** — the articles, *and* the `raw/` sources underneath them

## 4. Report

Give the answer inline and link the saved file.
