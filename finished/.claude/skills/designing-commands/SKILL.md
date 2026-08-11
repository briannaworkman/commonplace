---
name: designing-commands
description: Use when someone wants to add their own slash command to this vault — most often /query (ask the wiki a question), but also /lint, /gaps, /weekly, or anything else. Guides them through the design decisions that make it theirs, then writes the command file. Trigger on "help me write a command", "build my query command", "I want a command that…", "how do I add a slash command", or any request to create something in .claude/commands/.
---

# Designing a command for this vault

Someone wants a command of their own. **Your job is to help them design it, not to hand them
a standard one.** The decisions are the substance of the exercise — a generic command they
didn't choose teaches them nothing.

## Before you ask anything

Read `.claude/commands/ingest.md`. That is the house shape: frontmatter with a
`description`, numbered stages, a check-your-work stage, a report stage. Match it.

## How to run this — read this part carefully

**Ask every design question in ONE message, as a compact numbered menu with short options.**

Do not ask one question at a time. Do not walk them through it conversationally. They are
probably in a workshop with minutes to spare, and a five-turn interview will burn the whole
block. One message, they reply once, you write the file.

If they answer only some questions, pick sensible defaults for the rest, then **say which
ones you chose for them** so they know what to go change.

If they say "just pick for me" — do it, but afterwards tell them the two choices most worth
revisiting and why. They should leave knowing which knobs exist.

## The questions for `/query`

Present these as options, with what each one buys. Keep the whole menu under ~15 lines.

1. **How far should it follow links?** Only the articles the index points at / one hop out
   along `[[wikilinks]]` / keep going while things look relevant. Shallow is fast and
   focused; deep finds forgotten connections and sometimes wanders.
2. **Should backlinks count for anything?** In Obsidian, what points *at* an article is as
   visible as what it points to. An article with many inbound links is probably load-bearing;
   one with a single inbound link is probably a detail. Options: ignore direction / prefer
   heavily-linked articles as more central / follow backlinks outward too.
3. **What happens at the edge of the wiki?** Refuse flatly / answer the part it can and mark
   where the wiki stops / also name the specific source they'd need to ingest. The last one
   turns every unanswerable question into a reading list.
4. **Save every answer, or only on request?** Always writing to `outputs/` builds a record of
   what they've asked; on-request keeps the folder clean.
5. **What should the output look like?** Prose with inline links / a citations table / include
   the path it took through the graph. Showing the path is how they catch it reading the
   wrong articles.

There is no right answer to any of these. Do not recommend one set. If they ask what you'd
pick, say what you'd pick *and* what it costs.

## For a command that isn't `/query`

Ask three things instead: what should trigger it, what should it read, and what should it
change or produce. Then the same closing questions — what does it do when it finds nothing,
and does it write a file or just report.

Useful ones to suggest if they're stuck: `/lint` (repair broken links and orphans), `/gaps`
(list questions the wiki *can't* answer yet), `/weekly` (what got added and what it connected
to).

## Writing the file

- Path: `.claude/commands/<name>.md`. Adding the file *is* installing the command.
- Frontmatter needs `description:`. If the command takes an argument it also needs
  `argument-hint:`, and the body **must** contain `$ARGUMENTS` where the input lands.
  Without it the command silently runs with no input — this is the single most common
  failure, so never omit it.
- Reference `CLAUDE.md` for things that are always true (frontmatter schemas, the naming
  rule). Do not restate them in the command; that is duplication that will drift.
- Put their actual choices in the text as instructions. "Follow wikilinks one hop out from
  the articles the index suggests" — not "follow links as appropriate."
- Keep it in plain English. No code.

## After writing it

Three things, in this order:

1. **Tell them to open the file and read it.** This matters more than running it. They should
   see that their decisions are sitting there in plain sentences they can edit.
2. Point out that this skill is also just a markdown file, at
   `.claude/skills/designing-commands/SKILL.md`. Same idea one level up — they can open it,
   change it, or write their own.
3. Suggest they run it, and try one question the wiki covers well and one it doesn't, so they
   see both behaviours.

Do not do the command's job by hand. If they ask for a command, they get a file.
