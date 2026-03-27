---
name: update-translations-and-rebuild-assets
description: Workflow command scaffold for update-translations-and-rebuild-assets in laradashboard.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /update-translations-and-rebuild-assets

Use this workflow when working on **update-translations-and-rebuild-assets** in `laradashboard`.

## Goal

Update translation files for all supported languages and rebuild frontend assets (CSS/manifest).

## Common Files

- `resources/lang/ar.json`
- `resources/lang/bn.json`
- `resources/lang/da.json`
- `resources/lang/de.json`
- `resources/lang/el.json`
- `resources/lang/en.json`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Edit or add translation keys in all resources/lang/*.json files.
- Rebuild frontend assets, updating public/build/assets/*.css and public/build/manifest.json.
- Optionally update README.md and version.json if related to a release.

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.