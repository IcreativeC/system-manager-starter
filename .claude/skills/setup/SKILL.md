---
name: setup
description: The install wizard for this workspace. Use when the user types /setup, asks to set up or personalize this folder, or agrees to run setup from the bootstrap greeting. Also handles re-runs — changing earlier answers or starting over.
---

# /setup — the install wizard

You are an installer. Behave like one: numbered pages — label them "Step N of 4" on the
Express path or "Step N of 5" on Custom, counting About you · Projects · Memory ·
[Preferences] · Ready — one page per message, friendly and plain; the user may never have
used a terminal before. **Write
NOTHING to disk until the final "install" confirmation.** All answers live in the
conversation until then. If the user disappears mid-interview, nothing has changed and
`/setup` restarts clean — that is by design.

## Step 0 — has setup already run?

Read the first line of the root `CLAUDE.md`:
- Contains `BOOTSTRAP — setup has not run` → fresh install. Go to Page 1.
- Contains `personalized on` → already set up. Say: "You're already set up. Want to
  **(1)** change some answers, **(2)** start completely over, or **(3)** never mind?"
  - **(1) Reconfigure:** read `_setup/answers.md`, show the pages as a list, re-ask only
    the pages they pick, then continue at the Ready page with old answers filled in for
    everything untouched.
  - **(2) Start over:** run the full interview; the final write replaces everything as in
    a fresh install. Warn first: starting over discards any edits made to `CLAUDE.md` since
    setup - git keeps them only if backup is on.
  - **(3)** Stop. Touch nothing.

## Page 1 — Welcome (no questions)

> Welcome! I'm going to set up this folder as your personal home base — a place where I
> remember who you are, what you're working on, and how you like to work. About 10 minutes,
> and nothing is saved until you approve a summary at the end.
>
> **1) Express setup** — 5 quick questions, sensible defaults *(recommended)*
> **2) Custom setup** — 10 questions, more control
>
> Which one?

## Page 2 — About you (both paths)

- Q1: "What's your first name — and is that what I should call you, or do you go by
  something else?"
- Q2: "In a sentence or two: what do you spend most of your time on these days? Work,
  school, hobbies — whatever's true."

## Page 3 — Your projects (both paths)

- Q3: "When you hear 'projects,' what kind of stuff comes to mind for you? Pick any that
  fit: **(a)** school / classes **(b)** gaming **(c)** a small business or side hustle
  **(d)** creative stuff — music, art, writing, videos **(e)** life admin — house, money,
  health, plans **(f)** a mix / something else."
- Q4: "Name 2 or 3 things you're actually working on (or want to be) right now — one line
  each. Example: 'learn guitar', 'plan the spring trip', 'fix my resume'. These become
  your first registered projects."
  - **If they name nothing** ("nothing", "not sure", a shrug): ask once more, plainly —
    "No problem. What's one thing you'd want help with this week?" If that is still
    nothing, say: "Okay — your project list will start with one placeholder row so it's
    never empty; the first thing you bring up in a session goes there." Then move on.
    Never write a bare table (see the write pass).

## Page 4 — Memory and boundaries (both paths)

- Q5: "Is there anything I should *always* remember about you — the stuff you'd be
  annoyed to repeat every time? (Schedule, family, tools you use, things you never want
  suggested.) Totally fine to say 'nothing yet.'"
- Q-B (the boundary): "Last one on this page. **Outside this folder**, may I **(a)** read
  only, **(b)** change things when you approve each one, or **(c)** go ahead? Most people
  pick (b)." If they shrug or skip it, use **(b)**.

**Express path ends here.** Apply defaults: answer style = *short answer first, details on
request* · git backup = **off** · wrap-up reminders = **on (gentle)**. Go to the Ready page.

## Page 5 — Preferences (Custom only)

- Q6: "How do you like answers? **(a)** Short and direct — just tell me **(b)** Explain
  your reasoning as you go **(c)** Step-by-step instructions I can follow."
- Q7: "For each project you named: is it *active* right now, *on hold*, or *just an
  idea*?" (one compact list)
- Q8: "Want me to back this folder up with **git** — a save-history tool — so nothing is
  ever lost? It stays on this computer. **(a)** Yes **(b)** No **(c)** What's git?" — on
  (c), explain in one plain paragraph, then re-ask. (A private GitHub backup can be
  connected later — mention it only if they ask.)
- Q9: "There's a `/wrap-up` command that files away what we learned at the end of a
  session. Want me to **(a)** remind you to run it when we seem done **(b)** leave it to
  you **(c)** skip the habit entirely?"
- Q10: "Last one — anything about tone? Formal or casual, emoji or none, pet peeves?
  (Optional.)"

## Final page — Ready to install

Show an installer-style review: name · one-line bio · project list with statuses · memory
items · boundary answer · answer style · git backup on/off · reminders on/off. Then:

> Type **install** to create your workspace, or tell me anything to change.

## The write pass (only after they type "install") — single pass, this exact order

**Tools, pinned:** write every file with the **Write** tool (it is pre-allowed for this
folder, so it never prompts). The only shell commands in this whole skill are the git
lines in step 7 — never write a file through the shell.

Fill `{{PLACEHOLDERS}}` from the answers — exact mappings, nothing invented. Use plain
ASCII punctuation in everything you write (a hyphen, not a long dash; straight quotes):

- `{{DATE}}` = today, YYYY-MM-DD · `{{NAME}}` = Q1 · `{{BIO}}` and `{{Q2_ANSWER}}` = Q2 in
  their own words
- `{{STYLE}}` = one sentence from Q6 plus any Q10 tone notes; Express default, verbatim:
  `Short answer first; expand only if I ask.`
- `{{GIT_BACKUP}}` and `{{REMINDERS}}` = the literal word `on` or `off` — the wrap-up
  skill reads these values, so don't get creative
- `{{REMINDER_RULE}}` = if reminders are on, verbatim: `When a session winds down, gently
  suggest /wrap-up once - don't nag.` If off: omit the line entirely.
- `{{AUTHORITY}}` = exactly one of these three lines, from Q-B:
  - (a) `Outside this folder I may read only.`
  - (b) `Outside this folder I may change things when you approve each one.`
  - (c) `Outside this folder I may go ahead.`
- `{{ALWAYS_REMEMBER}}` = Q5 items **verbatim, in their words** (no rephrasing, no
  trimming), one bullet per line, each indented two spaces (`  - fact`) so they nest under
  "Always remember:"; if nothing: `  - nothing recorded yet`
- `{{ABOUT_SUMMARY}}` = Q2, then ` Always remember: ` and the Q5 items joined with `; `.
  If Q5 is empty, Q2 alone.
- `{{PROJECT_ROWS}}` = one `| name | Status | what it is |` row per Q4 project — "what it
  is" stays in the user's own phrasing (if they gave only a name, repeat the name); don't
  embellish; Express: every status `Active`. **If Q4 ended with nothing**, exactly one row:
  `| First project | Idea | Nothing named at setup - the first thing you bring up in a session goes here; /wrap-up will offer it. |`

1. Copy the current root `CLAUDE.md` to `_setup/original-CLAUDE.md` (skip if that file
   already exists — never overwrite it).
2. Write `_setup/answers.md` in this shape (every question asked, answer verbatim; omit
   lines for questions that were not asked on this path):
   ```
   # Setup answers (personalized on YYYY-MM-DD)
   Path: Express
   Q1 Name: ...
   Q2 Spends time on: ...
   Q3 Projects mean: ...
   Q4 Projects:
   - name - what it is      (just the name if that is all they gave; never repeat it)
   Q5 Always remember:
   - fact                   (verbatim)
   Q-authority: (b) change things when you approve each one
   Q6 Answer style: ...   (Custom only; likewise Q7 statuses, Q9 reminders, Q10 tone)
   Q8 Git backup: off
   Defaults applied: answer style = short first; wrap-up reminders = on.
   ```
3. Write `memory/about-me.md` from `_setup/templates/memory-about-me.template.md`.
4. Write `memory/MEMORY.md` from `_setup/templates/MEMORY.template.md`.
5. Write `projects/projects.md` from `_setup/templates/projects.template.md` — one row
   per named project (Custom: use their statuses; Express: all `Active`).
6. Write the root `CLAUDE.md` from `_setup/templates/CLAUDE.template.md` — this replaces
   the bootstrap and is the moment the folder becomes theirs.
7. Git hygiene, silently and only if a `.git` folder exists: run exactly
   `git remote remove origin` — nothing appended, no redirection. A "No such remote"
   error is expected and fine (a ZIP-download folder has none; so does a folder set up
   for someone else). If they opted INTO git backup: if `git config user.email` prints
   nothing, first run `git config user.name "<Q1 name>"` and
   `git config user.email "<Q1 name, lowercased, no spaces>@localhost"` (repo-local, so
   the first commit cannot fail on a fresh machine); then `git add -A` and commit
   `workspace created by /setup`. If git isn't installed at all: skip everything in this
   step and (if they opted in) mention in one friendly line that backup needs git and can
   be set up later — do not treat it as an error.

## Finish page

List the files just created (and, if Q4 was empty, say the project list holds one
placeholder row), then:

> Three things to try right now:
> ① Ask me anything about one of your projects.
> ② Tell me a fact about yourself — at the next `/wrap-up` you'll see it land in memory.
> ③ When you're done today, type `/wrap-up`.
>
> To change any of these answers later, just type `/setup` again.

## Rules

- Never write outside this folder.
- Never ask for passwords, payment details, or accounts beyond what's already signed in.
- If the folder path contains "OneDrive", warn once on Page 1: cloud-synced folders can
  fight the files here; recommend moving the folder later (link them to README's advice).
- One page per message. Never dump the whole interview at once.
