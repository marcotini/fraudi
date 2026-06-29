# Setup

Two paths depending on where you use Claude. The skill works on both.

---

## Path A — Claude.ai (web or mobile)

No terminal, no files on disk. There are two ways to do this; the first is recommended because it uses fraudi as a real skill (all personas and lenses come along, and Claude picks what fits your opening message).

### Option 1 (recommended) — Upload it as a Skill

Claude.ai now supports skills natively at [claude.ai/customize/skills](https://claude.ai/customize/skills) (Settings → Customize → Skills).

1. Download this repository as a `.zip` (on GitHub: **Code → Download ZIP**), or zip your local clone of the `fraudi` folder.
2. Go to [claude.ai/customize/skills](https://claude.ai/customize/skills)
3. Click **Upload skill** and select the `fraudi` zip
4. Enable it

That's the whole setup. Because the upload includes `SKILL.md` plus every persona and lens, fraudi reads your opening message and selects the persona+lens that fit — same behavior as Claude Code. You don't paste anything by hand.

To use it, just start talking about whatever you're reflecting on. To stop, say *"switch off fraudi"* or disable the skill in settings.

### Option 2 — Build it from a Style

Use this if you'd rather assemble the mode by hand, or you want a single fixed persona+lens that never changes.

### Step 1 — Create a Style

1. Open claude.ai
2. Go to Settings → Styles → Create a Style
3. Name it `fraudi` (or whatever you want)
4. Paste the contents of [`SKILL.md`](../SKILL.md) into the style instructions
5. Save

### Step 2 — Pick a persona

Open the persona file you want — for example [`modes/personas/flint.md`](../modes/personas/flint.md) — and append its contents to the same style. You can swap personas later by editing the style.

### Step 3 — Optionally pick a lens

Same move with a lens file. Append the contents of e.g. [`modes/lenses/pattern.md`](../modes/lenses/pattern.md) to the style.

A style with `SKILL.md` + one persona + one lens is the recommended starting setup.

### Step 4 — Use it

When you want to use reflection mode, switch the active style at the bottom of the chat input to `fraudi`. Switch it back to default for everything else.

### Step 5 (optional) — Use a Project

If you want one persistent space for reflection (recommended), create a Project called something like "reflection" and put the style instructions in the Project's custom instructions instead of (or in addition to) the Style.

The advantage of a Project: every chat in it starts with the same context, and you can add files to the Project that Claude reads at the start of every conversation. See [`memory.md`](memory.md) for that.

---

## Path B — Claude Code (terminal)

Use this if you already use Claude Code and want the skill to be available globally.

### Step 1 — Clone

```bash
git clone https://github.com/marcotini/fraudi.git ~/.claude/skills/fraudi
```

### Step 2 — Use it

The skill auto-loads when invoked. To invoke:

```
use fraudi
```

or

```
reflection mode
```

You don't have to pick a persona or lens — fraudi reads your opening message and picks what fits. If you want to override, name them explicitly:

```
use fraudi with slow and ifs
```

You can also switch mid-conversation: *"switch to coach,"* *"use the somatic lens,"* *"drop the lens."*

### Step 3 — Memory

See [`memory.md`](memory.md) for the optional file-based memory layer if you want session continuity.

---

## Verification

After setup, test it. Open a chat and say something deliberately vague, like *"I've been feeling kind of off this week."*

If Claude responds with "I hear you, that sounds difficult, can you tell me more about what's been going on?" — the skill isn't loaded.

If Claude responds with something like "Off how? Give me one specific moment from this week." — it's working.

---

## Switching modes mid-conversation

You can ask Claude to switch persona or lens during a conversation:

> *Switch to slow.*
>
> *Use the somatic lens for this thread.*
>
> *Drop the lens, just observe.*

This works but adds context bloat over a long session. For sustained shifts, start a new chat with the new mode loaded.
