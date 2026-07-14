# AGENTS.md — ZuluBetterHeroes Reforged

MechWarrior 5: Mercenaries mod. Part of Chris's mod collection under
[`gitpush-mod`](https://github.com/gitpush-mod).

## What this is

Reforged version of the ZuluBetterHeroes MW5 mod. Historical design + iteration
notes live in `NOTES.md` next to this file.

## For agents

- **Game:** MechWarrior 5: Mercenaries (Unreal Engine 4)
- **Knowledgebase (READ FIRST):** [`gitpush-mod/mw5-knowledgebase`](https://github.com/gitpush-mod/mw5-knowledgebase)
  — MW5 engine details, common patterns, gotchas. The `reference/ZuluBetterHeroes/`
  folder in the knowledgebase preserves the ORIGINAL ZuluBetterHeroes raw source
  as a reference for how this project was structured before the Reforged rebuild.
- **MW5 skill:** planned, not built yet.

## Structure (standard MW5 mod plugin layout)

- `Config/` — UE4 config
- `Content/` — mod assets (packed on cook)
- `Resources/` — mod icon / thumbnail
- `ModOverride/` — override files
- `<ModName>.uplugin` — UE4 plugin metadata
- `mod.json` — MW5 mod manifest

Build output (`Saved/`, `Intermediate/`, `Build/`) is regenerable and gitignored
— GitHub's 100 MB file cap blocks the `Metadata/DevelopmentAssetRegistry.bin`
file that UE4 cooking produces.

## MUST NOT

- Modify vanilla MW5 game files
- Commit `Saved/`, `Intermediate/`, or `Build/` folders (gitignored)
- Overwrite files under the knowledgebase's `reference/` — that's the raw
  original ZuluBetterHeroes source, preserved as-is for study

## Related

- Knowledgebase: [`gitpush-mod/mw5-knowledgebase`](https://github.com/gitpush-mod/mw5-knowledgebase)
- Original source (reference): `mw5-knowledgebase/reference/ZuluBetterHeroes/`
- Parent when checked out under Chris's tree: `mods/mw5-mods/` / `mods/AGENTS.md`
