# claude-skills

Chris Deever's Claude Code skills, shared across Deevnet, EdS and their projects. The repository
is a Claude Code plugin marketplace, so every machine gets the same skills with one setup step.

## Setup on a new machine

```bash
claude plugin marketplace add cdeever/claude-skills
claude plugin install cd@cdeever-skills
```

Or, inside a session: `/plugin marketplace add cdeever/claude-skills`, then
`/plugin install cd@cdeever-skills`. The repository is private, so the machine needs
git access to GitHub (`gh auth login`, or an SSH key).

To pick up changes: `claude plugin marketplace update cdeever-skills`.

## The `cd` plugin

Every skill here is in one plugin, `cd`, so each one is typed `/cd:<skill>`. Type `/cd` to list
only these, apart from Claude Code's own commands. Add a new skill as
`plugins/cd/skills/<name>/SKILL.md`.

Structure at the start of an idea, light everywhere after it:

| Skill | Use it when |
|---|---|
| `/cd:ideation` | A new idea appears. It interviews you on the problem, scope, MVP and versions, and writes a proposal |
| `/cd:version-planning` | A proposal is accepted, or a version closes. It cuts versions, fixes each version's definition of done, and writes the plan and roadmap item |

The flow: idea → **ideation** (proposal) → **version planning** (versions, each with a definition
of done, then the plan) → ADRs and change records → **waypoints** reached → a version's definition
of done met, a **milestone**.

The skills are generic. Each repository's `CLAUDE.md` says where its proposals, roadmap and plans
live, and the skills follow it.

## Developing

```bash
claude plugin validate .
claude --plugin-dir ./plugins/cd   # try a change without installing it
```
