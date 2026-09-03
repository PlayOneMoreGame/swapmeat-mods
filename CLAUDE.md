# CLAUDE.md — swapmeat-mods

Guidance for Claude Code working in **this** repository. Read it before changing anything here.

## What this repository is

A **read-only export** of SWAPMEAT's shipped localization: the five official language packs under
`localization/official/` and the English source strings under `localization/_reference/`, regenerated from the
game's string tables when a release ships. It exists so players can **fork it** and build their own language
mods from a known-good starting point. It is public. It is not where localization work happens.

- **Source of truth is the game**, in the private `rog` repo (`rog/Assets/Content/Text/*.asset`). Nothing in
  `localization/official/` or `localization/_reference/` is authored here. Every file there is derived output.
- **Pull requests are disabled** on this repository, deliberately. Nothing flows from here back into the game,
  and a change committed here by hand is overwritten by the next export. Community translators keep their own
  forks and ship their packs themselves (mods folder or Steam Workshop).
- `localization/EXPORT.json` names the game release, date and source commit the current content came from.
  It is written by the export; do not edit it.

## How content gets here (the only way)

Content arrives by **direct push to `main`** from a rog checkout, after a localization drop has shipped in the
game. There is no branch-and-PR step in this repo, because PRs are off. The full procedure lives in rog's
`/import-loc-batch` skill (Step 12); the short form:

```bash
# in the rog repo, on main, with the Unity editor open on main and EditorBridge enabled
omg loc export-packs --mods-repo <path-to-this-checkout>   # regenerates official/, _reference/, EXPORT.json
# in this repo
scripts/validate                                          # the loader-shape check; must print "All packs valid."
git -C <this-checkout> diff --stat localization           # review: expect the drop's rows, nothing surprising
git add localization && git commit && git push origin main
```

Rules for that push:

- **Only after the drop has shipped.** The public copy must never run ahead of what players have. If the rog
  loc-drop PR has not merged and been released, do not push.
- **Only from an export.** Never hand-edit a CSV or a `.mod.json` here to "fix" a translation; fix it in the
  game's tables through the loc pipeline and re-export. A hand edit is silently lost on the next export and,
  until then, misrepresents what the game ships.
- **Review the diff before pushing.** A regeneration should show the drop's changed rows and little else.
  Hundreds of reordered lines means the exporter's row order changed; stop and look.
- **Docs are the exception.** `README.md`, `CONTRIBUTING.md`, this file and `scripts/` are authored here and may
  be edited and pushed directly, with the same care as any public-facing text.

## What lives where

```
localization/
  EXPORT.json    — release, date and source commit of the current export (written by the exporter)
  official/      — swapmeat-<locale>.{mod.json,UIStrings.csv,GeneratedStrings.csv} for es, pt-BR, ja, ko, zh-Hans
  _reference/    — en.UIStrings.csv, en.GeneratedStrings.csv: the English to translate a new language from
  glossary.csv   — established renderings of names and key terms (also exported from rog)
scripts/validate — structural check: manifest valid, author present, both CSVs present, headers start "Key,Id,"
.github/workflows/validate.yml — runs scripts/validate on every push to main
```

## Things that look like work here but are not

- **A translation is wrong.** That is a rog change: fix the game's tables via the loc pipeline
  (`/loc-engineer` in rog), ship it, re-export.
- **Someone opened a PR.** They cannot; if a stale one exists, close it and point them at CONTRIBUTING.md. Do not
  merge anything into `main` that did not come from the exporter.
- **A key is missing from a pack.** Check EXPORT.json's release first: the pack matches that release, and a
  string added to the game after it lands with the next export.
- **The `files` block in a manifest does not match a CSV.** The exporter computes those checksums from the bytes
  it writes; a mismatch means someone edited a CSV by hand after export. Re-export rather than patching the hash.

## Style

Public-facing text here follows the same rules as SWAPMEAT's player-facing copy: plain sentences, no em dashes,
no marketing register. Explain, do not sell. Contributors are hobbyist translators, not developers; assume no
programming background in the README and CONTRIBUTING.
