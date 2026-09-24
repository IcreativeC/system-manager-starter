---
name: wrap-up
description: End-of-session close-out for this workspace. Use when the user types /wrap-up, says they're done, wrapping up, heading out, or asks to file away the session. Graduates durable facts to memory, refreshes the project list, optionally commits a backup, and ends with a short summary.
---

# /wrap-up — file the session away

Top rule: **every step is optional-on-failure.** A wrap-up that only manages step 4 is
still a wrap-up. Never end in an error state — end in the summary. The owner is leaving:
**ask at most one question in the whole wrap-up**, and only when a wrong guess would be
worse than a wrong answer. Otherwise act, and say what you did.

## 1. Graduate durable facts

Scan this session for things worth remembering past today — facts about the owner,
decisions they made, preferences they showed. For each:
- **New topic** → new file in `memory/` (short kebab-case name, one topic per file) + a
  row in `memory/MEMORY.md`'s index.
- **Existing topic** → edit that file (and its index row's summary if it changed). Never
  add a duplicate file for a fact that already has a home.
Session-only chatter dies with the session, on purpose. When unsure whether something is
durable, file it and name it in the summary — the owner can delete the line.

### 1b. Index check
List every `memory/*.md` file and compare against the index table in `memory/MEMORY.md`
(paths are relative to the workspace root, e.g. `memory/about-me.md`). Any file without a
row gets one now (topic = the file's first heading, summary = its first bullet). Any row
whose file is missing is named in the summary, not deleted.

## 2. Refresh the project list

For any project touched today: update its Status and one-liner in
`projects/projects.md`. If a new effort came up in conversation, **add it as an `Idea`
row and announce it** ("added 'X' as an Idea — delete the line if you don't want it")
instead of asking. If the list still holds the setup placeholder row ("First project")
and a real project came up today, replace the placeholder with it. Done projects get
Status `Done` and **stay** — rows are history, not clutter. Only a *destructive* change
(removing or renaming a row the owner made) gets a question.

## 3. Back up — only if CLAUDE.md's Settings say git backup is on

`git add -A`, then commit: `wrap-up YYYY-MM-DD: <five-word summary>`. Push only if a
remote exists — if backup is on but there is no remote, say so in one line ("backed up on
this computer only - no GitHub connection yet") so they know their history lives only on
this machine. If git is missing or anything here fails: one friendly line ("backup
skipped — <reason>") and move on. **Never fail the wrap-up over backup.**

## 4. Summary

One short screen: what we did today · what went into memory · project list changes ·
**anything changed outside this folder this session** (files, settings, installs — list
each, or say "nothing outside this folder") · one suggested next step for next time. End
with: "See you next time."
