# Changelog

All notable changes to this skill will be documented here.

The format is loosely based on [Keep a Changelog](https://keepachangelog.com/).

## [Unreleased]

### Added

- `modes/lenses/attachment.md` — relational patterns around closeness and distance
- `modes/lenses/compassion.md` — self-criticism as a system, names the critic without flattering

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
