# Pre-flight: from zero to ready in ~15 minutes

Follow these in order. Every step ends with a ✅ check — don't move on until the check
passes. If a friend is helping you, they can read this aloud and drive.

> **Who this is for:** a personal computer you control (Windows or Mac). A managed work
> laptop that blocks installers won't work — stop here and use a personal machine instead.

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

- **With git:**
  ```
  git clone https://github.com/IcreativeC/system-manager-starter.git system-manager
  ```
- **Without git** (no idea what git is? use this path): on the GitHub page, green **Code**
  button → **Download ZIP** → extract it to the location above, and rename the folder to
  `system-manager` if you like.

✅ **Check:** the folder contains `README.md` and a `.claude` folder (hidden files may need
"show hidden items" turned on — or just trust the README being there).

## 6. Run the wizard

Open a terminal **in that folder** (Windows: open the folder in File Explorer, click the
address bar, type `powershell`, Enter · Mac: drag the folder onto Terminal), then:

```
claude
```

and type:

```
/setup
```

Answer the questions — about 5 minutes, and nothing is saved until you approve the summary
at the end. Welcome home. 🏠
