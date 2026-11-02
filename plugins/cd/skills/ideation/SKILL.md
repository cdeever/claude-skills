---
name: ideation
description: Shape a new idea before any decision or plan exists. Use when the owner has a new idea for a project, service or component ("EdS needs its own music inventory", "what if the Pi lab ran its own builds"), wants to explore one, or asks to ideate. Interviews the owner about the problem, scope, MVP and versions, a few questions at a time, and writes a proposal page. Writes no ADRs, change records, roadmap items or plans; version-planning comes after.
argument-hint: "[the idea, in a sentence]"
---

# Ideation

An idea becomes a **proposal**: a page that says what the idea is for, what it is and is not, the
smallest version worth having (the MVP), and a rough cut of the versions after it. Ideation comes
before any ADR, change record, roadmap item or plan. Those come from the `cd:version-planning` skill
once the owner accepts the proposal.

The owner decides. Your job is to ask the questions that give the idea edges, offer options where
the owner hesitates, and write down what was decided. Do not invent scope the owner did not ask
for. A good idea found along the way goes in the proposal's **Later** list, not into the MVP.

## 1. Find where proposals go

Read the repository's `CLAUDE.md` for where proposals live and how pages are written: voice,
headings, link style, spelling. Follow those rules over anything here.

- If it names a place (EdS: `docs/content/docs/architecture/proposals/`), use it.
- If it names none, ask the owner. Suggest `architecture/proposals/` beside the ADRs.

Then read what already exists: other proposals, the ADRs and records the idea touches, and any
roadmap item near it. Bring what you find into the interview ("ADR-0046 already matches requests
against the library; would the inventory take that over?").

## 2. Interview

Ask a few questions at a time, three or four at most, with options where they help. Use the
`AskUserQuestion` tool when it is available. Each round builds on the answers before it. Skip a
question the owner already answered.

1. **The problem.** What is wrong or missing today? Who or what feels it? Why now?
2. **The shape.** What is it, in one sentence? Where does it run, and what does it talk to? Which
   existing system is its customer, and which does it replace or take a job from?
3. **The boundary.** What is it *not*? What stays the job of something else? Which sources stay
   the truth for what they hold?
4. **The MVP.** What is the smallest thing that is useful end to end, to a real user or system?
   What would the owner use on the first day?
5. **Versions.** What would v1 (the MVP), v2 and "later" be, roughly? Test each: is it one
   coherent step someone would notice?
6. **Risks and unknowns.** What could make it not worth doing? What must be found out first?
   Which decisions will need ADRs?

Stop when the MVP has clear edges and the owner agrees with the version cut. Leave anything
unresolved as an open question rather than guessing.

## 3. Write the proposal

One page, written in the repository's voice. The status is **Proposal**: not decided and not
built.

```markdown
---
title: "A <Thing>"
---

# Proposal: A <Thing>

| | |
|---|---|
| **Status** | Proposal, not decided and not built |
| **Date** | YYYY-MM-DD |
| **Where** | <the repository or service it lives in, and where it runs> |
| **Would extend** | <ADRs and records it builds on or would replace, linked> |

<One paragraph: what it is, and who its customer is.>

## Why

<The problem today, concretely: what is asked where, and how it fails.>

## What it is

<Bulleted, each bullet a bold full-sentence lead-in.>

## What it is not

<The boundary: what stays someone else's job.>

## The MVP

<The smallest useful thing, end to end, and what the owner does with it on the first day.>

## Versions

- **v1, the MVP:** <one line>
- **v2:** <one line>
- **Later:** <the ideas worth keeping that are not in v1 or v2>

## Open questions

<What must be decided or found out, each with who decides or how.>
```

Show the owner the page before you commit it. Then commit and open a pull request by the
repository's rules. Do not merge it.

## 4. Hand off

Say what comes next: once the owner accepts the proposal, run the `cd:version-planning` skill on it.
That skill turns the version cut into versions with a definition of done, and writes the roadmap
item and plan. Do not write those here.
