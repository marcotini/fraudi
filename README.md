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

1. Copy the contents of [`SKILL.md`](SKILL.md) into a new Style at claude.ai → Settings → Styles
2. Optionally, create a Project for reflection and paste your chosen persona + lens into the Project instructions

Full walkthrough in [`docs/setup.md`](docs/setup.md).

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

**Lenses** — pick zero or one:
- `pattern` — default. Watches for recurrence across what you say.
- `cbt` — thought records, cognitive distortions, evidence checks.
- `act` — values, defusion, what you're avoiding.
- `ifs` — parts language. The protector, the exile, the manager.
- `somatic` — attention to body and sensation.
- `narrative` — the story you're telling about yourself, and who the author is.
- `behavioral` — what you actually did vs. what you said you'd do.
- `bias` — Kahneman-flavored. Spots cognitive distortions in your reasoning about yourself.

All in [`modes/`](modes/).

---

## A note on the name

`fraudi` is not respectful to Freud. It isn't trying to be. The point is to make the name do work the README otherwise has to do: this is a Freud-shaped object, not Freud. A reflection of a reflection. Don't mistake one for the other.

If the name bothers you, the skill probably isn't for you. That's fine.

---

## License

MIT. See [`LICENSE`](LICENSE). Do what you want with this. Fork it. Rewrite it. If you make it better, send a PR.
