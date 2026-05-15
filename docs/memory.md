# Memory between sessions

The skill works fine without any memory layer — Claude reads your conversation, observes, and forgets when the chat closes. For a lot of people that's enough. For some it isn't.

If you want Claude to open a session with *"last time you said you'd talk to your sister. did you?"* — you need a persistent file-based memory layer. This document describes how to set one up.

---

## The principle

Three rules govern the memory layer:

1. **Plain markdown files on disk.** Not vector databases, not embeddings, not cloud APIs. Markdown. You can open them in any editor. You own them.
2. **A rolling profile, not an append-only log.** One file that gets *rewritten* over time. Captures patterns, themes, where you are now. Stays lean.
3. **Per-session notes, kept separate.** Each session gets its own file. Claude reads the recent ones, not all of them.

---

## Directory structure

```
my-reflection/
├── CLAUDE.md              # tells Claude what to do at session start
├── profile.md             # rolling summary of you (gets rewritten)
├── sessions/
│   ├── 2026-01-15.md      # one file per session
│   ├── 2026-01-28.md
│   └── 2026-02-07.md
└── notes/                 # optional: anything else you want loaded
    └── values.md
```

For Claude Code: put this anywhere and point Claude Code at it.

For Claude.ai: put `profile.md` and the latest 2–3 session files into your Project files. After each session, update them manually (or have Claude generate the update and you copy it in).

---

## CLAUDE.md template

This is the file Claude reads first. It tells Claude how to handle the rest.

```markdown
# Session start protocol

Before responding to the user's first message in this session:

1. Read `profile.md` for context about who I am and what we've been working on.
2. Read the 2 most recent files in `sessions/` for recent threads.
3. Identify one specific commitment, intention, or open thread from the last session that warrants follow-up.
4. Open with that follow-up. One question. No preamble.

# Session end protocol

When I say "wrap up" or "end session":

1. Generate a session summary as a new file in `sessions/` named `YYYY-MM-DD.md`.
   Sections: What we covered. Patterns noticed. What I said I'd do. Open threads.
   Keep it under 300 words.
2. Update `profile.md` with anything that genuinely changed our understanding.
   Do not append — rewrite the relevant sections. Keep profile.md under 1000 words total.
3. Show me the updated profile.md and the new session file before saving.

# Skill rules

[Paste the contents of SKILL.md here]

# Persona

[Paste the contents of your chosen persona here]

# Lens

[Paste the contents of your chosen lens here, if any]
```

---

## profile.md template

This file is the rolling summary. It should be lean, current, and rewritten — not appended to.

```markdown
# Profile

Last updated: 2026-02-07

## Who I am, briefly
[2-3 sentences. Age range, life context, what brought me here.]

## What we're working on
[2-4 active threads. Things that have come up repeatedly. Each one a sentence or two.]

## Patterns we've named
[Patterns Claude has observed that I've confirmed. Each one a sentence with one example.]

## Commitments still open
[Things I said I'd do that I haven't done yet, or am in the middle of.]

## What to avoid
[Topics I've asked Claude not to push on, or that need a real human.]

## Style notes
[How I prefer Claude to engage with me. Calibration learned over sessions.]
```

The first session populates this file. Every subsequent session can update it.

---

## sessions/YYYY-MM-DD.md template

```markdown
# Session — 2026-02-07

## Covered
[What we talked about. One paragraph.]

## Patterns noticed
[New observations, or old ones with new evidence. Bullet list, brief.]

## What I said I'd do
[Concrete commitments. Bullet list with deadlines if any.]

## Open threads
[Things we didn't finish or chose to come back to.]
```

---

## On scaling

The concern: doesn't this file grow forever and bloat the context window?

The answer: no, because the profile is a *summary*, not a log. It gets rewritten. The session files do accumulate, but Claude only reads the recent ones at session start. Older sessions are still on disk for you to read, but they're not in Claude's context.

In practice: a year of weekly reflection should produce ~50 short session files and a profile that stays under 1000 words. That's nothing.

---

## On privacy

These files are on your disk. If you put them in a cloud-synced folder (iCloud, Dropbox, Google Drive), they're now also in the cloud. If you use Claude.ai's Project files, they're on Anthropic's servers — read [Anthropic's privacy policy](https://www.anthropic.com/legal/privacy) and decide if you're okay with that.

A common solution: use Claude Code with the files purely local. Most paranoid solution: don't write down anything you wouldn't be okay with appearing in a leak.

---

## A warning

A persistent memory layer makes the skill significantly more powerful. It also makes it significantly more attached-to-able. People who run setups like this sometimes describe the experience of "Claude knowing me better than my therapist" — and depending on your context, that's either useful or a warning sign.

If you notice you're going to your reflection chat instead of going to people in your life, the file is doing too much work. Consider taking it apart for a while.
