---
title: "Loops, Graphs, and When to Nest One Inside the Other"
source_type: link
source_url: "https://medium.com/codetodeploy/loops-graphs-and-when-to-nest-one-inside-the-other-e877084275f5"
captured: 2026-08-12
---

# Loops, Graphs, and When to Nest One Inside the Other

_Brianna Workman — CodeToDeploy (Medium), August 2026_

A practical framework for agent orchestration in Claude Code, distinguishing two
complementary approaches for automating agent work at different scales.

## Loop engineering

A loop automates a single agent's iterative cycle: attempt a task, verify the result,
adjust, retry. The pattern follows reason–act–observe–reason again. Five components are
essential: measurable completion criteria, external verification, layered termination
conditions, persistent state, and human checkpoints. Loops work best for repeating tasks
with clear pass/fail criteria — CI-failure triage, dependency updates.

## Graph engineering

Graphs coordinate multiple independent agents working in parallel on different aspects of
a problem. Rather than sequential steps, a graph identifies the real dependencies between
tasks and runs everything non-dependent simultaneously. The "diamond" topology — fan work
out, process independently, merge results — typically improves performance across most
jobs.

## The critical distinction

Loops optimize vertically (one agent, repeated refinement); graphs optimize horizontally
(many agents, parallel execution). The **fake-edge test** decides which applies: if step B
genuinely consumes step A's output, keep them ordered; otherwise run them simultaneously.

## Nesting

When discovery work has unknown scope, nest a loop inside a graph as a single node. The
loop handles open-ended discovery — finding bugs until no new ones emerge — and the graph's
verification stage then validates all findings in parallel. The hybrid combines iterative
depth with breadth-parallel validation.

_Archived from https://medium.com/codetodeploy/loops-graphs-and-when-to-nest-one-inside-the-other-e877084275f5_
