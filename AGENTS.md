# AGENTS.md — ZuluBetterHeroes Reforged

MechWarrior 5: Mercenaries mod. Part of Chris's mod collection under
[`gitpush-mod`](https://github.com/gitpush-mod).

## What this is

Reforged version of the ZuluBetterHeroes MW5 mod. Historical design + iteration
notes live in `NOTES.md` next to this file.

## Where work lives (RULE — non-negotiable)

**Every task on this mod is a ticket on its project board.** YOU (the agent) create the ticket BEFORE touching anything. No exceptions for "small" work.

**Board:** [ZuluBetterHeroes Reforged board](https://github.com/orgs/gitpush-mod/projects/11)

Concrete rules — same as TCS ticket-first:

- **Starting work?** Open a ticket in this repo, add to the board, set Status = **In Progress**, then start.
- **Have an idea for later?** Ticket in **Backlog**. Not in memory, not in a README, not in NOTES.md.
- **Need Chris to check something before closing?** Move the ticket to **In QA** and comment with exactly what he needs to look at. Do NOT set to Done — that's Chris's call after review.
- **Finished?** Close the ticket with a closing summary comment (what you did / problems + solutions / anything NOT done).
- **Same-session micro-work?** Open + close in the same session — but the ticket exists.
- **Older than 30 days in Done?** The weekly cron in this repo moves it to Archived. The closed ticket + CHANGELOG entry persist.

Automation: closing a Done ticket auto-appends an entry to this repo's `CHANGELOG.md` (via the workflow in `gitpush-mod/.github`). Requires `MOD_PROJECT_TOKEN` org secret — already installed.

**Do NOT** work on this mod without a ticket. If Chris asks for something small, create + immediately-close the ticket. It's still faster than the paper-trail debt of un-ticketed work.

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

## How to verify (before flagging In QA or closing)

- **Cook the mod** via the MW5 Mod Editor's `Manage Mod → Package Mod`. Errors block the closing.
- **Load in a fresh MW5 career save.** Verify the mod appears in the Mod Manager, enables cleanly, and doesn't crash the loading screen.
- **In-mission smoke test.** For pilot/character mods: hire the pilot (or trigger the unlock), fly one mission, listen for voice lines, verify portrait renders. For trait/system mods: check the cantina UI, buy a trait, verify effect.
- **No vanilla-asset copies** — this is critical for anything visual/audio. All art and audio in the mod is original or open-licensed.
- **Check `%LOCALAPPDATA%\MW5Mercs\Saved\Logs\`** — any errors mention the mod? Quote them in the ticket.

## MUST NOT

- Modify vanilla MW5 game files
- Commit `Saved/`, `Intermediate/`, or `Build/` folders (gitignored)
- Overwrite files under the knowledgebase's `reference/` — that's the raw
  original ZuluBetterHeroes source, preserved as-is for study

## Related

- Knowledgebase: [`gitpush-mod/mw5-knowledgebase`](https://github.com/gitpush-mod/mw5-knowledgebase)
- Original source (reference): `mw5-knowledgebase/reference/ZuluBetterHeroes/`
- Parent when checked out under Chris's tree: `mods/mw5-mods/` / `mods/AGENTS.md`
