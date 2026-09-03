# Making your own language for SWAPMEAT

This repository is a starting point, not a destination. It holds the language packs that ship with
[SWAPMEAT](https://store.steampowered.com/app/2246060/) and the English text they were translated from, exported
from the game every release (`localization/EXPORT.json` names the release). **It does not accept pull requests**:
a change merged here would simply be overwritten by the next export. What you make is yours to keep and ship.

No Unity, no programming, no build. A translation is a spreadsheet of text.

## The flow

1. **Fork** this repository.
2. **Edit the text in your fork:**
   - *Improve a language SWAPMEAT ships* — open its pack under `localization/official/`, e.g.
     `swapmeat-zh-Hans.UIStrings.csv`, and fix the values. Give the pack your own base name and `author` so it
     shows up as yours in the game (see the format below); don't leave it named like the official one.
   - *Add a language SWAPMEAT doesn't ship* — copy the English source from `localization/_reference/`, name the
     files `<yourname>-<locale>.UIStrings.csv` and `<yourname>-<locale>.GeneratedStrings.csv`, add a
     `<yourname>-<locale>.mod.json`, and translate the value column.
3. **Check it** with `scripts/validate` (Bash + Python 3; it checks the three files agree and the headers are
   right).
4. **Ship it.** Drop the three files into the game's `mods/` folder to play it yourself or hand it to friends
   (see the README for the folder), or publish the pack on the Steam Workshop so anyone can subscribe. The
   game lists community packs in **Options → Language** with a `[MOD]` tag and your `author`.

## The file format

Each language is **three files that share a base name**, e.g. `mytag-ja.mod.json`, `mytag-ja.UIStrings.csv`,
`mytag-ja.GeneratedStrings.csv`:

- **`<base>.mod.json`** — the manifest. Required fields: a `name`, an **`author`** (the game shows it in the
  language picker so players can tell two translations of the same language apart), and a `localization` block
  with the language `locale` (a [BCP-47] code like `ja`, `pt-BR`, `zh-Hans`) and a `displayName`. For example:
  ```json
  {
    "schemaVersion": 1,
    "name": "Better Chinese",
    "author": "your-name",
    "localization": { "locale": "zh-Hans", "displayName": "中文" }
  }
  ```
  The official packs also carry a `files` block with each CSV's size and SHA-256. That is optional: the game
  verifies it when present and loads the pack without it.
- **`<base>.UIStrings.csv`** and **`<base>.GeneratedStrings.csv`** — the text. Columns are `Key, Id,
  <Language>(<locale>)`. **Translate only the value column.** Leave `Key` and `Id` exactly as they are — they
  match the string to the game.

## Rules that keep a pack working

- **Don't touch `Key` or `Id`.** They're the game's link to each string.
- **Leave placeholders alone.** Anything in `{curly braces}`, `[SquareBrackets]`, or `<angle brackets>` is a
  variable or markup the game fills in — copy it through untouched. Reordering or translating it breaks the
  string.
- **Keep names consistent.** Character, creature, and place names have established translations in
  `localization/glossary.csv`. You are free to disagree with ours in your own pack; the glossary is there so you
  can be consistent with yourself.
- **A missing translation is fine.** Any value you leave blank falls back to the official text, then to
  English, in-game — partial translations are welcome and playable.

## Keeping up with game updates

Every SWAPMEAT release re-exports this repository, so `_reference/` and `official/` always match the current
game. New or changed strings show up as new or changed rows. Pull the update into your fork, translate the
rows that changed, and re-publish your pack. A key you have not translated yet falls back to English, so a
pack is never broken by a game update, only incomplete.

[BCP-47]: https://www.rfc-editor.org/info/bcp47
