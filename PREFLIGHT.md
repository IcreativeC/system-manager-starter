# Pre-flight: from zero to ready in ~15 minutes

Follow these in order. Every step ends with a ✅ check — don't move on until the check
passes. If a friend is helping you, they can read this aloud and drive.

> **Who this is for:** a personal computer you control (Windows or Mac). A managed work
> laptop that blocks installers won't work — stop here and use a personal machine instead.

## 0. How this works (30 seconds)

Claude does not carry a conversation forward on its own - each session starts fresh. This
folder is what it reads first every time, so what is written here is what it knows about
you. `/wrap-up` is how today gets written down for tomorrow.

## 1. Claude account — and the honest cost

Go to [claude.ai](https://claude.ai) and sign up (or sign in).

This setup runs on **Claude Code**, which needs the **Pro plan — about $20/month**
(≈$17/month billed yearly; [claude.ai/pricing](https://claude.ai/pricing) has the current
number).

**Not ready to pay today?** That's a fine answer. Here's what you'd be getting, so you can
decide later:
- An assistant that actually remembers you between sessions
- A project list that keeps itself current
- Everything in plain files you own — nothing locked in

Bookmark the repo and stop here; nothing below requires payment to read.

✅ **Check:** claude.ai shows **Pro** on your account (click your initials, bottom-left).

## 2. Install Claude Code

**Windows** — open PowerShell (Start menu → type "powershell" → Enter) and run:

```
irm https://claude.ai/install.ps1 | iex
```

**Mac** — open Terminal (Cmd+Space → type "terminal" → Enter) and run:

```
curl -fsSL https://claude.ai/install.sh | bash
```

If your machine blocks the installer and you happen to have Node.js:
`npm install -g @anthropic-ai/claude-code`

When it finishes: **close the terminal window and open a NEW one.** (This is the fix for
almost every "claude is not recognized" error — the new window picks up the install.)

✅ **Check:** in the NEW terminal, `claude --version` prints a version number.

## 3. Sign in

Run:

```
claude
```

A browser window opens asking you to log in — use the account from step 1. (If it doesn't
open, type `/login` inside Claude Code.)

✅ **Check:** type `/status` inside Claude Code — it shows your account, on Pro.

## 4. Hello session

Still inside Claude Code, type: *"introduce yourself in two sentences."*

✅ **Check:** it answers. Type `/exit` to leave.

## 5. Get the starter folder

Put it in your home folder — `C:\Users\<you>\system-manager` (Windows) or
`~/system-manager` (Mac). **Not** Documents or Desktop if OneDrive/iCloud syncs them —
cloud sync fights this setup.

- **Download ZIP (the default - use this unless you already use git):** on the GitHub page,
  green **Code** button → **Download ZIP** → extract it to the location above. The extracted
  folder is called `system-manager-starter-main`; rename it to `system-manager`.
- **With git** (only if you already have it):
  ```
  git clone https://github.com/IcreativeC/system-manager-starter.git system-manager
  ```

✅ **Check:** the folder contains `README.md`. (There's also a `.claude` folder — on Mac,
press Cmd+Shift+. in Finder to see dot-files — but seeing README.md is proof enough.)

## 6. Run the wizard

**Desktop app (Claude Desktop):** open this folder as a project in the Code tab, then type
`/setup` — you can skip the terminal instructions below.

**Terminal:** open a terminal **in that folder** (Windows: open the folder in File Explorer,
click the address bar, type `powershell`, Enter · Mac: in Terminal type `cd ` — with a
trailing space — then drag the folder into the window and press Enter), then:

```
claude
```

and type:

```
/setup
```

Answer the questions — about 10 minutes, and nothing is saved until you approve the summary
at the end. Welcome home. 🏠
