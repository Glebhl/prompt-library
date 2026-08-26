# Upstream provenance

This directory vendors the `impeccable` skill from:

- Repository: https://github.com/pbakaus/impeccable
- Source path: `.github/skills/impeccable`
- Commit: `63b04e2530f5c7b41ea83c133daab24f34912456`
- Retrieved: 2026-08-26
- Upstream skill version: `4.1.2`

The upstream skill files are copied without modification except for
`SKILL.md`. Its YAML frontmatter was adapted for Codex compatibility: the
upstream `version` and `argument-hint` values were moved into supported
`metadata`, and the unsupported `user-invocable` field was removed. A prominent
modification notice is included in that file as required by Apache License 2.0,
section 4(b).

The following files were added locally to retain provenance and applicable
license notices next to the vendored copy:

- `LICENSE` — upstream Apache License 2.0 text.
- `NOTICE.md` — upstream third-party notice.
- `THIRD_PARTY_LICENSES/modern-screenshot-MIT.txt` — MIT license for the
  vendored `modern-screenshot` 4.7.0 distribution in
  `scripts/modern-screenshot.umd.js`.
- `THIRD_PARTY_LICENSES/platform-design-skills-MIT.txt` — MIT license for the
  source acknowledged by the upstream `NOTICE.md`.
