# system-manager-starter

**Your own personal home base for Claude Code** — a folder where Claude remembers who you
are, what you're working on, and how you like to work. Set up by answering a few questions
in an install-wizard-style walkthrough. Everything ends up in plain files you can open,
edit, and delete yourself.

## How this works

Claude does not carry a conversation forward on its own - each session starts fresh. This
folder is what it reads first every time, so what is written here is what it knows about
you. `/wrap-up` is how today gets written down for tomorrow.

## What you get

- A personalized `CLAUDE.md` — Claude reads it at the start of every session, so you never
  re-introduce yourself
- A `memory/` folder — facts about you and your life that Claude keeps up to date
- A `projects/` list — the things you're working on, with statuses that stay current
- A `/wrap-up` command — end a session with everything filed away

No accounts beyond Claude itself, no cloud services required, no telemetry. Just files in
a folder you own.

## What you need (the honest part)

1. **A computer you control** (Windows or Mac — not a locked-down work laptop)
2. **A Claude account with the Pro plan** — about **$20/month** (check
   [claude.ai/pricing](https://claude.ai/pricing) for the current number). Claude Code, the
   tool this runs on, needs a paid plan. Not ready to pay today? Totally fine — bookmark
   this page and come back.
3. **15 minutes**

Never used a terminal before? That's expected. The setup holds your hand the whole way.

## Getting started

**Starting from zero (no Claude account yet)?** Open [PREFLIGHT.md](PREFLIGHT.md) and follow
it top to bottom — it walks you from nothing to ready, with a ✅ check at every step.

**Already have Claude Code installed and signed in?**

1. Get this folder onto your computer, in your home folder — for example
   `C:\Users\<you>\system-manager` on Windows or `~/system-manager` on Mac.
   *(Avoid Documents or Desktop if OneDrive or iCloud syncs them — cloud sync and this
   setup fight each other.)*
   - With git: `git clone https://github.com/IcreativeC/system-manager-starter.git system-manager`
   - Without git: green **Code** button above → **Download ZIP** → extract it there
2. Open a terminal in that folder and run: `claude` — or, in the Claude desktop app, open
   this folder as a project in the Code tab
3. Type: `/setup`

That's it. The wizard takes about 10 minutes, shows you a summary before it writes anything,
and nothing is saved until you approve it.

## After setup

- Just talk to Claude — ask about your projects, plan your week, whatever you'd use it for
- When a session winds down, type `/wrap-up` — that's what keeps the memory and project
  list current
- Change your answers anytime by typing `/setup` again
- One folder, one branch. If the app offers to work in a separate copy of this folder, say
  no — or bring your changes back before you `/wrap-up`, so they land in the memory Claude
  actually reads

## License

MIT — see [LICENSE](LICENSE). Share it with your friends.
