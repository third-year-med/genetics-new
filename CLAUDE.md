# CLAUDE.md — a module of the Interactive Pathology Teaching Platform

This repository is one module (a single `index.html`): **Genetics and Pediatric Diseases (New)** (module key `genenew`, storage
prefix `gn_`, card after Genetics on the front page). Built 2026-11-17 as a VERY condensed (~28 %), separate version of
`third-year-med/genetics` (that module is unchanged), with the same app code.

The platform's decisions, the checklist for modules, the deployment steps, the testing workflow and the lessons learned are
in the platform repository: `third-year-med/Interactive-pathology-platform` → `CLAUDE.md` and `docs/HANDBOOK.md` (§4.2.7;
rebuilds: `docs/REBUILD.md`).

- The course data in `index.html` is encrypted with this module's OWN content key, which lives only in the user's Code.gs
  (`CONTENT_KEYS.genenew`). Never commit a key or an unencrypted copy of the course.
- The `<script id="platform-nav">` block is maintained in the platform repo (`modules/platform-nav.js`) and written here
  with `tools/module-release.js refresh` — do not edit it by hand.
- Stable IDs: topics t01–t10 (t10 = Integration; no Practical topic), sections sNNMM, questions q001–q148 (selected from
  Genetics; the old id is in each question's `sourceRef`), cases c01–c08. A new build keeps them (`docs/REBUILD.md`).
- Source of truth for conflicting facts: Robbins Basic Pathology 10th ed., Chapter 7.
- The Robbins picture-import file (`neo-picture-import`, keys `gnew-robbins-01…20`) and the viva bank
  `genetics-new-viva-bank.json` (50 questions `viva_gn_tNN_NN`) are delivered to the user directly and never committed.
- Test changes on the real page with the platform repo's e2e test "Genetics and Pediatric Diseases (New) module (genenew)"
  (`GN_CONTENT_KEY` in the environment) and `node test/module-smoke/smoke.js` before pushing.
