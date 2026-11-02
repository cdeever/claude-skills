---
name: version-planning
description: Turn an accepted proposal, or a project already under way, into versions with a fixed definition of done, then shape its roadmap item and project plan. Use when the owner accepts a proposal, starts building a new project, finds a project that never says when it is done, or closes a version and wants the next one cut. Guards against scope creep by putting new ideas in the next version instead of widening the current one.
argument-hint: "[the proposal or project, e.g. 'eds-inventory' or a path]"
---

# Version planning

A project is built one **version** at a time. Each version has a short **definition of done**,
written before its work starts, that says when the version is finished. Scope creep is welcome: it
is how good ideas arrive. But a new idea becomes part of the **next** version, never a reason the
current one cannot finish. When the definition of done is met, the version is done, and that is a
**milestone**.

The words this skill uses:

- **Waypoint**: a piece of work finished, often one decision or change. Tasks feed it.
- **Milestone**: the waypoint that closes a version, because its definition of done is met.
- **Task**: a short step in the plan.

## 1. Read

- The repository's `CLAUDE.md`: where roadmap items and plans live, their format, and any skill
  that keeps them. In deevnet-docs, that is a roadmap item with a `waypoints:` list, its
  `plan.md`, and the `roadmap-update` skill. Follow those rules over anything here.
- The proposal (from the `ideation` skill), if there is one, and its version cut.
- What already exists: the item and plan, if any; the ADRs, change records and waypoints already
  reached. On a project under way, the work done shows where v1 really stands.

## 2. Cut the versions

Propose the cut to the owner and settle it, a few questions at a time (`AskUserQuestion` when
available):

- **v1 is the MVP**: the smallest thing useful end to end. Each later version is one coherent step
  someone would notice.
- For **each version**: a one-line goal, then its **definition of done**: 3–6 points, each an
  outcome someone could check ("The store recollected from iTunes on schema v1", not "work on the
  importer"). Say how each is checked when that is not obvious.
- For **each version**, what it is **not**, named so it has somewhere to go.
- Only the current version needs a full definition of done. Later versions get a goal and a sketch.
  Their definition of done is written when they become current.

## 3. Freeze the current version

Once the owner agrees, the current version's definition of done is **fixed**:

- **A new idea goes to the next version** by default. Add it to that version's list, or to
  **Later**.
- **Changing a definition of done is the owner's deliberate call**, never a quiet edit. If the
  owner decides something truly belongs in this version, change the point, and add a dated note
  under the list saying what changed and why.
- **A point found impossible or pointless** is struck by the owner, the same way, with a note.

## 4. Write the plan

Write the versions into the project plan, in the plan's existing format. In deevnet-docs, the
plan is `<item>/plan.md`. Version headings carry **no** ✅ 🔄 ⏳ emoji, because those count as
tasks there. Their status is a word, and the definition of done uses checkboxes:

```markdown
## Versions

### v1, the MVP (current)

<Goal, one line.>

**Done when:**

- [ ] <checkable outcome>
- [ ] <checkable outcome>
- [ ] <checkable outcome>

**Not in v1:** <what goes to v2 or later>

### v2 (next)

<Goal, one line, and a short sketch. Its definition of done is written when it becomes current.>

### Later

- <ideas worth keeping>
```

Then the phases and tasks for the **current version only**, in the plan's usual form. A later
version gets its tasks when it becomes current.

## 5. Shape the roadmap item

Where the repository keeps a roadmap:

- The item states the project's intent and lists its **waypoints**. Add one planned waypoint for
  each definition-of-done point that reads as an outcome. In deevnet-docs, use the `roadmap-update`
  skill's format and `waypoints.py`.
- Add the **closing waypoint** as planned, with `milestone: true`: "<Project> v1 done: <goal>". It
  is marked done the day the last point is met.
- List the decisions v1 needs (the ADRs to write) and the changes it expects (the change records),
  as tasks in the plan. They are written as the work reaches them, not now.

## 6. Check and propose

Show the owner the versions, the frozen definition of done, and the waypoints. Run the
repository's checks (deevnet-docs: `waypoints.py check`, then the `hugo-docs` skill). Commit and
open a pull request by the repository's rules. Do not merge it.

## When a version closes

When every point of the current definition of done is checked:

1. Check the points off in the plan. Mark the closing waypoint done with the day the last point
   was met. In deevnet-docs, use `waypoints.py done`, and keep `milestone: true`.
2. Make the next version current: write its definition of done from its sketch and the ideas
   gathered while the last version was built (section 2), then freeze it (section 3), and write
   its tasks (section 4).
3. Ideas still left over stay in **Later**.

Run this skill again to cut the next version. It is the one place a future version's definition
of done is written.
