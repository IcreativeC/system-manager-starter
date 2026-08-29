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
    a fresh install.
  - **(3)** Stop. Touch nothing.

## Page 1 — Welcome (no questions)

> Welcome! I'm going to set up this folder as your personal home base — a place where I
> remember who you are, what you're working on, and how you like to work. About 5 minutes,
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

## Page 4 — Memory (both paths)

- Q5: "Is there anything I should *always* remember about you — the stuff you'd be
  annoyed to repeat every time? (Schedule, family, tools you use, things you never want
  suggested.) Totally fine to say 'nothing yet.'"

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
items · answer style · git backup on/off · reminders on/off. Then:

> Type **install** to create your workspace, or tell me anything to change.

## The write pass (only after they type "install") — single pass, this exact order

Fill `{{PLACEHOLDERS}}` from the answers — exact mappings, nothing invented:

- `{{DATE}}` = today, YYYY-MM-DD · `{{NAME}}` = Q1 · `{{BIO}}` and `{{Q2_ANSWER}}` = Q2 in
  their own words
- `{{STYLE}}` = one sentence from Q6 plus any Q10 tone notes; Express default: "Short
  answer first; expand only if I ask."
- `{{GIT_BACKUP}}` and `{{REMINDERS}}` = the literal word `on` or `off` — the wrap-up
  skill reads these values, so don't get creative
- `{{REMINDER_RULE}}` = if reminders are on: "When a session winds down, gently suggest
  /wrap-up once — don't nag." If off: omit the line entirely.
- `{{ALWAYS_REMEMBER}}` = Q5 items as bullets, or "nothing recorded yet"
- `{{ABOUT_SUMMARY}}` = one line combining Q2 and Q5
- `{{PROJECT_ROWS}}` = one `| name | Status | what it is |` row per Q4 project — "what it
  is" stays in the user's own phrasing, don't embellish; Express: every status `Active`

1. Copy the current root `CLAUDE.md` to `_setup/original-CLAUDE.md` (skip if that file
   already exists — never overwrite it).
2. Write `_setup/answers.md`: date, Express/Custom, every question and answer verbatim.
3. Write `memory/about-me.md` from `_setup/templates/memory-about-me.template.md`.
4. Write `memory/MEMORY.md` from `_setup/templates/MEMORY.template.md`.
5. Write `projects/projects.md` from `_setup/templates/projects.template.md` — one row
   per named project (Custom: use their statuses; Express: all `Active`).
6. Write the root `CLAUDE.md` from `_setup/templates/CLAUDE.template.md` — this replaces
   the bootstrap and is the moment the folder becomes theirs.
7. Git hygiene, silently and only if a `.git` folder exists: `git remote remove origin`
   (their folder must stop pointing at the public starter repo; ignore a "No such remote"
   error — a ZIP-download folder has none). If they opted INTO git
   backup: `git add -A` and commit `workspace created by /setup`. If git isn't installed
   at all: skip everything in this step and (if they opted in) mention in one friendly
   line that backup needs git and can be set up later — do not treat it as an error.

## Finish page

List the files just created, then:

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
