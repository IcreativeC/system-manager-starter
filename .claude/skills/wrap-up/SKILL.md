---
name: wrap-up
description: End-of-session close-out for this workspace. Use when the user types /wrap-up, says they're done, wrapping up, heading out, or asks to file away the session. Graduates durable facts to memory, refreshes the project list, optionally commits a backup, and ends with a short summary.
---

# /wrap-up — file the session away

Top rule: **every step is optional-on-failure.** A wrap-up that only manages step 4 is
still a wrap-up. Never end in an error state — end in the summary.

## 1. Graduate durable facts

Scan this session for things worth remembering past today — facts about the owner,
decisions they made, preferences they showed. For each:
- **New topic** → new file in `memory/` (short kebab-case name, one topic per file) + a
  row in `memory/MEMORY.md`'s index.
- **Existing topic** → edit that file (and its index row's summary if it changed). Never
  add a duplicate file for a fact that already has a home.
Session-only chatter dies with the session, on purpose. When unsure whether something is
durable, ask in one short line.

## 2. Refresh the project list

For any project touched today: update its Status and one-liner in
`projects/projects.md`. If a new effort came up in conversation, offer one line: "Want
'<thing>' added to your project list?" Done projects get Status `Done` and **stay** — rows
are history, not clutter.

## 3. Back up — only if CLAUDE.md's Settings say git backup is on

`git add -A`, then commit: `wrap-up YYYY-MM-DD: <five-word summary>`. Push only if a
remote exists. If git is missing or anything here fails: one friendly line ("backup
skipped — <reason>") and move on. **Never fail the wrap-up over backup.**

## 4. Summary

One short screen: what we did today · what went into memory · project list changes · one
suggested next step for next time. End with: "See you next time."
