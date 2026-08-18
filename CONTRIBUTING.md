# Contributing translations

Thank you — this is the whole point of the repo. Players localize SWAPMEAT better than we did, and this is how
your work gets into the game.

No Unity, no programming, no build. A translation is a spreadsheet of text.

## The flow

1. **Fork** this repo and make a branch.
2. **Edit the text:**
   - *Improve a language we ship* — open its file under `swapmeat/localization/official/`, e.g.
     `omg-zh-Hans.UIStrings.csv`, and fix the values.
   - *Add a language we don't ship* — copy the English source from `swapmeat/localization/_reference/` into
     `swapmeat/localization/community/`, name it `<yourname>-<locale>.UIStrings.csv` (and
     `…GeneratedStrings.csv`), add a `<yourname>-<locale>.mod.json`, and translate the value column.
3. **Open a pull request.** Automated checks run on it (below). If one fails, it tells you exactly what to fix.
4. A maintainer reviews the green PR and merges. Merged languages ship in the next game update and, later, on
   Steam Workshop.

## The file format

Each language is **three files that share a base name**, e.g. `omg-ja.mod.json`, `omg-ja.UIStrings.csv`,
`omg-ja.GeneratedStrings.csv`:

- **`<base>.mod.json`** — the manifest: the language `locale` (a [BCP-47] code like `ja`, `pt-BR`, `zh-Hans`)
  and the `displayName` shown in the game's language picker.
- **`<base>.UIStrings.csv`** and **`<base>.GeneratedStrings.csv`** — the text. Columns are `Key, Id,
  <Language>(<locale>)`. **Translate only the value column.** Leave `Key` and `Id` exactly as they are — they
  match the string to the game.

## Rules the checks enforce

- **Don't touch `Key` or `Id`.** They're the game's link to each string.
- **Leave placeholders alone.** Anything in `{curly braces}`, `[SquareBrackets]`, or `<angle brackets>` is a
  variable the game fills in — copy it through untouched. Reordering or translating it breaks the string.
- **Keep names consistent.** Character, creature, and place names have established translations in
  `glossary.csv`. The check flags drift from them.
- **A missing translation is fine.** Any value you leave blank falls back to English in-game — partial
  translations are welcome and playable.

## Your grant to us (please read)

By opening a pull request, you grant One More Game a perpetual, worldwide, irrevocable, royalty-free license to
use, modify, publish, and distribute your contribution as part of SWAPMEAT and One More Game's other products
and channels (including Steam Workshop). You confirm the work is yours to give and isn't copied from a
copyrighted translation. You keep the right to your own work; you're giving us permission to ship it. See
[LICENSE](LICENSE).

[BCP-47]: https://www.rfc-editor.org/info/bcp47
