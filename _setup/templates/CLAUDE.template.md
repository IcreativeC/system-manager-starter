<!-- system-manager-starter: personalized on {{DATE}} -->
# {{NAME}}'s Workspace

## What this folder is
{{NAME}}'s home base. Claude reads this file at the start of every session here.
Everything in this folder is plain files {{NAME}} can open, edit, or delete - nothing is
hidden, nothing is locked in.

## About me
{{BIO}}

## My projects
The list lives in `projects/projects.md` - check it when I mention a project, and keep it
current. Any project can grow its own folder under `projects/`.

## Memory
Read `memory/MEMORY.md` at the start of a session. Durable facts about me live in
`memory/` (one topic per file). New facts land there during `/wrap-up`, not mid-session.

## Places
- `README.md` - what this folder is and how to get started again
- `PREFLIGHT.md` - the from-zero setup checklist (account, install, sign in)
- `memory/` - facts about me, one topic per file, indexed in `memory/MEMORY.md`
- `projects/` - my project list; new project folders go under `projects/<name>/`
- `_setup/` - my setup answers and the original bootstrap file (leave it alone)

## Boundaries
{{AUTHORITY}}

## How I like answers
{{STYLE}}

## Settings
- git backup: {{GIT_BACKUP}}
- wrap-up reminders: {{REMINDERS}}

## Wrapping up
{{REMINDER_RULE}}
To change any of these answers, type `/setup`.
