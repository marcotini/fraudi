# fraudi

> A reflection skill for Claude. Not a therapist. The name is the disclaimer.

```
fraudi = Freud + fraud
```

It admits in the title what most "AI therapist" tools won't: this is not therapy. It's a structured mirror with the flattery stripped out.

---

## What this does

When you use Claude for self-reflection, processing emotions, spotting patterns in your own behavior — the default Claude is too soft. Too much "I hear you." Too much "that sounds really hard." Too many follow-up questions packed into one turn. Too much therapy-speak that sounds wise but doesn't land.

This skill replaces that mode with a set of operational rules. A taste:

- No preamble, no sign-off, no validation rituals
- One question per turn
- Name patterns flat, with no softening adverbs
- Concrete metaphor over psychological jargon
- Distinguish what you *observe* from what *resonates*
- Notice the question behind the question
- Vague answers get pushed back on with "give me a specific example"
- Never accept the role of "therapist" — even if asked

And one rule above all: if the conversation enters crisis territory, drop the mode entirely and be plainly human about pointing to real help.

The full ruleset (Rule 0 plus ten numbered rules) is in [`SKILL.md`](SKILL.md).

---

## Why this exists

This skill takes the opposite bet from default Claude: constrain the wrapper, keep the substance. The architectural argument — why a role makes Claude generic and a task doesn't — is in [`docs/why-not-therapist.md`](docs/why-not-therapist.md).

---

## What this is not

- Not therapy
- Not a diagnostic tool
- Not a crisis line
- Not a replacement for a human you trust

If you are in crisis, in active self-harm, in an abusive situation, or experiencing acute psychiatric symptoms — close this repo and call someone real. The skill itself is designed to step out of its own mode in those moments, but you should not be relying on a markdown file to catch you.

If you are already doing real reflection work — with a therapist, a journal, a steady inner life — this might sharpen what you already do. That's the entire intended use case.

---

## Install

### For Claude.ai (web/mobile)

Upload it as a native skill at [claude.ai/customize/skills](https://claude.ai/customize/skills): download this repo as a `.zip` (**Code → Download ZIP** for the latest, or the pinned [v0.3.0 archive](https://github.com/marcotini/fraudi/archive/refs/tags/v0.3.0.zip)), then **Upload skill**. All personas and lenses come along, so inference works the same as in Claude Code.

Prefer a hand-built Style instead? That path still works — full walkthrough in [`docs/setup.md`](docs/setup.md).

### For Claude Code

```bash
git clone https://github.com/marcotini/fraudi.git ~/.claude/skills/fraudi
```

The skill auto-activates when invoked, or trigger it manually with natural language: *"use fraudi"* or *"reflection mode."*

### For memory between sessions

The skill works without any memory layer. If you want continuity — Claude opening a session with *"last time you said you'd talk to your sister. did you?"* — see [`docs/memory.md`](docs/memory.md) for the optional file-based memory layer.

---

## Modes

Personas (how Claude sounds) and lenses (what Claude focuses on) are modular and combinable. **You don't need to pick one** — fraudi reads what you say and chooses the fit. Tell it "I had a bad day at work" and it'll pick `flint` + `pattern`. Say "part of me wants to call her, part of me doesn't" and it'll switch to `ifs`. You can override at any time ("use fraudi with slow and somatic," "switch to coach," "drop the lens").

**Personas** — pick one:
- `flint` — default. Friction, not warmth. Short. Direct. Spots patterns flat.
- `slow` — contemplative. More breathing room between observations.
- `dry` — observational and slightly cool. Anthropologist of self.
- `socratic` — almost only questions. Rarely states.
- `coach` — action-oriented. Closes most turns with a concrete next move.
- `mirror` — reflects what you said with one small shift. No interpretation. Lets you hear yourself.
- `devil` — argues the strongest version of the other side. Opt-in only; stress-tests a held position.

**Lenses** — pick zero or one:
- `pattern` — default. Watches for recurrence across what you say.
- `cbt` — thought records, cognitive distortions, evidence checks.
- `act` — values, defusion, what you're avoiding.
- `ifs` — parts language. The protector, the exile, the manager.
- `somatic` — attention to body and sensation.
- `narrative` — the story you're telling about yourself, and who the author is.
- `behavioral` — what you actually did vs. what you said you'd do.
- `bias` — Kahneman-flavored. Spots cognitive distortions in your reasoning about yourself.
- `attachment` — how you relate to closeness. Strategies, not styles.
- `compassion` — self-criticism as a system. Names the critic, doesn't flatter the user.
- `motivational` — ambivalence about change. Surfaces both sides without picking one.
- `existential` — meaning, mortality, freedom, isolation. For when the ache isn't psychological.

All in [`modes/`](modes/).

**How to tell it's on.** fraudi opens with a compact marker — `[fraudi · flint + pattern]` — telling you the skill is active and which persona + lens it inferred. It reappears only when the mode changes, and disappears entirely on a crisis turn (Rule 0 drops the mode). No marker at all means the skill isn't loaded.

---

## A note on the name

`fraudi` is not respectful to Freud. It isn't trying to be. The point is to make the name do work the README otherwise has to do: this is a Freud-shaped object, not Freud. A reflection of a reflection. Don't mistake one for the other.

If the name bothers you, the skill probably isn't for you. That's fine.

---

## License

MIT. See [`LICENSE`](LICENSE). Do what you want with this. Fork it. Rewrite it. If you make it better, send a PR.
