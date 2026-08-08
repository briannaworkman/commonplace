---
title: "Graph Engineering"
tags: [agents, orchestration, method]
updated: 2026-08-12
sources:
  - raw/links/Loops, Graphs, and When to Nest One Inside the Other.md
related: ["[[Loop Engineering]]", "[[Linked Thought]]"]
---

# Graph Engineering

Graph engineering coordinates multiple independent agents working in parallel on different
parts of a problem. Instead of laying work out as a sequence of steps, you identify the
*real* dependencies between tasks and run everything that isn't dependent at the same time.

## The fake-edge test

The question that decides the shape of the work: does step B genuinely consume step A's
output? If yes, the edge is real and the order must hold. If not, the edge is fake — an
artifact of how you happened to write the list — and the two should run simultaneously.

Most sequential plans are mostly fake edges. People write steps in the order they thought
of them, and that ordering then masquerades as a dependency.

## The diamond

The common topology is a diamond: fan the work out, process each branch independently,
merge the results. It improves throughput on most jobs because the merge is usually the
only genuine dependency in the whole plan.

## Vertical and horizontal

[[Loop Engineering]] optimizes *vertically* — one agent, refining repeatedly until a
criterion is met. Graph engineering optimizes *horizontally* — many agents, running at
once. They answer different questions: a loop asks "is this right yet?", a graph asks
"what doesn't need to wait?"

## The same argument as linked notes

The fake-edge test is [[Linked Thought]] applied to work instead of ideas. A folder
hierarchy imposes one location per idea when most ideas belong in several; a sequential
plan imposes one ordering on work when most steps have no ordering between them. In both
cases the structure is inherited from how the thing was written down rather than from
anything true about the material, and in both cases the fix is the same — keep only the
relationships that are real, and let everything else be adjacent.
