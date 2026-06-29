# Inference smoke test

A fast pass to check that the inference cues in `SKILL.md` actually fire in
production — and that the status marker reports the mode the cue should select.

The known issue (see `CLAUDE.md`): production sessions sometimes default to
`flint` + `pattern` even when a more specific cue is present. The status marker
makes this visible. This sheet turns that into a checklist.

## How to run

1. Load fraudi in a fresh session (Claude Code: `use fraudi`; web: enable the skill).
2. Paste one opener below as the **first** message of a new conversation.
3. Read the `[fraudi · …]` marker on the first turn and compare to **Expect**.
4. New conversation per row — inference keys off the opening message, so don't chain them.

A row passes if the marker matches **and** the response shows the lens's
signature move (named in `SKILL.md` under "Inference cues"). A matching marker
with a generic response is a partial pass — the mode was selected but the lens
didn't engage.

## Cases

| # | Opener | Expect |
|---|--------|--------|
| 1 | "I just had a garbage day, I need to vent." | `flint · pattern` |
| 2 | "I'm such an idiot, I completely blew the presentation." | `… · compassion` |
| 3 | "Whenever someone gets close I go quiet and pull back. I did it again." | `… · attachment` |
| 4 | "I keep saying I'll quit drinking and I just… don't." | `… · motivational` |
| 5 | "What's the point of any of this, honestly. Seriously asking." | `… · existential` |
| 6 | "Part of me wants to take the job, part of me is terrified of it." | `… · ifs` |
| 7 | "Every time I think about calling her my chest gets tight." | `… · somatic` |
| 8 | "I always screw up relationships. People like me don't get to keep things." | `dry · narrative` |
| 9 | "I bombed one interview so I'm clearly unemployable." | `… · bias` |
| 10 | "She hates me. I can tell she thinks I'm incompetent." | `flint · cbt` |
| 11 | "I keep meaning to go to the gym and I don't, I don't know why." | `flint · act` |
| 12 | "I just want to think out loud for a sec, don't analyze me." | `mirror` (no lens) |
| 13 | "I planned to write every day this week. Hold me to it." | `coach · behavioral` |
| 14 | "My dad died last month and I don't know how to be." | `slow` |

Rows 2–7 and 9 use `…` for the persona because persona is inferred separately
from tone and may vary; the **lens** is the thing under test. Row 12 should
carry no lens. Crisis openers are deliberately excluded — under Rule 0 the mode
drops and **no marker** should appear (see `human-scenarios.md` Scenario 3).

## Recording results

When a row fails, note the opener, the marker you actually got, and whether the
signature move was present. A cluster of misses that all collapse to
`flint · pattern` is the symptom of the known weak-inference issue — worth a
SKILL.md cue-wording pass, not a one-off fix.
