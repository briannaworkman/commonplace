---
title: "Loop Engineering"
tags: [agents, orchestration, method]
updated: 2026-08-12
sources:
  - raw/links/Loops, Graphs, and When to Nest One Inside the Other.md
related: ["[[Graph Engineering]]"]
---

# Loop Engineering

A loop automates a single agent's iterative cycle: attempt a task, verify the result,
adjust, retry. The shape is reason → act → observe → reason again, and it continues until
a stated criterion is met rather than until a fixed number of steps have run.

## What a loop needs to not run away

Five components, all of them load-bearing:

- **Measurable completion criteria** — "done" has to be checkable by something other than
  the agent's own opinion.
- **External verification** — a test, a linter, a build. Self-assessment is not evidence.
- **Layered termination conditions** — success, budget exhausted, no progress across N
  iterations. A loop with one exit will eventually fail to take it.
- **Persistent state** — so an iteration knows what the previous ones already tried.
- **Human checkpoints** — a place for a person to look before consequences compound.

Loops suit repeating work with clear pass/fail criteria: triaging CI failures, updating
dependencies, anything where you can tell mechanically whether the last attempt worked.

## Loops and graphs

A loop optimizes *vertically* — one agent going deeper on one problem.
[[Graph Engineering]] optimizes *horizontally* — many agents going wide at once. Neither
replaces the other, because they answer different questions.

## Nesting one inside the other

When discovery work has unknown scope, nest the loop inside the graph as a single node.
The loop does the open-ended part — finding bugs until a round turns up nothing new, which
no fixed step count could size in advance — and the graph's next stage verifies every
finding in parallel. Iterative depth where the scope is unknown, parallel breadth where
the work is already enumerated.
