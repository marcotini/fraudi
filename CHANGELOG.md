# Changelog

All notable changes to this skill will be documented here.

The format is loosely based on [Keep a Changelog](https://keepachangelog.com/).

## [0.3.0] — 2026-06-29

### Added

- Status marker: Claude opens with a compact `[fraudi · {persona} + {lens}]` tag on the first turn and again whenever the persona or lens changes, so the user can tell the skill is active and which modes were inferred (web clients give no other signal). It is a status tag, not preamble; Rule 0 (crisis) drops the mode and the marker with it.

### Changed

- SKILL.md mid-session switching is no longer fully silent — the switch turn now shows the status marker. Prose narration of the switch is still disallowed.
- `tests/human-scenarios.md` Scenario 2 and 3 updated to check marker presence (on switch) and absence (in crisis)

## [0.2.0] — 2026-05-16

### Added

- `modes/lenses/attachment.md` — relational patterns around closeness and distance
- `modes/lenses/compassion.md` — self-criticism as a system, names the critic without flattering
- `modes/lenses/motivational.md` — ambivalence about change, surfaces both sides
- `modes/lenses/existential.md` — meaning, mortality, freedom, isolation (Yalom / Frankl frame)
- `modes/personas/mirror.md` — reflects what the user said with one minimal shift, no interpretation
- `modes/personas/devil.md` — argues the strongest version of the other side; opt-in only
- Auto-selection of persona and lens from the user's opening message (SKILL.md inference cues)

### Changed

- SKILL.md now explicitly instructs Claude to load persona and lens files at invocation, with inference rules and silent mid-session switching
- README and setup docs reflect that picking a persona/lens manually is optional

## [0.1.0] — Initial release

### Added

- `SKILL.md` with Rule 0 (safety floor) and Rules 1–10 (operational rules)
- 5 personas: `flint`, `slow`, `dry`, `socratic`, `coach`
- 8 lenses: `pattern`, `cbt`, `act`, `ifs`, `somatic`, `narrative`, `behavioral`, `bias`
- `docs/why-not-therapist.md` — the architectural argument behind the skill
- `docs/setup.md` — install paths for Claude.ai and Claude Code
- `docs/memory.md` — optional file-based memory layer
- `examples/good-vs-bad.md` — paired examples showing the difference
- `examples/pillow-moments.md` — concrete metaphor reframes

### Known limitations

- No automated testing of skill behavior — every change requires manual verification across the modes
- Memory layer is documented but not packaged as a script
- All personas and lenses default to English; non-English use is possible but the rules will be enforced less consistently
- The skill cannot prevent Claude from being wrong; it can only make Claude less performatively warm
