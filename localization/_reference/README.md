# English source (`_reference/`)

The English strings to translate a **new** language from. Each file is `Key, Id, English(en)` — copy it,
rename to your language (`<yourname>-<locale>.UIStrings.csv`), replace the English value column with your
translation, and put it in [`../community/`](../community/). See [CONTRIBUTING](../../CONTRIBUTING.md).

> To *improve* a language SWAPMEAT already ships, you don't need these — edit the existing pack in
> [`../official/`](../official/) instead.

Two files, both `Key, Id, English(en)`, exported from SWAPMEAT's English string tables:

- `en.UIStrings.csv` — hand-authored UI text (menus, buttons, messages).
- `en.GeneratedStrings.csv` — item, ability, creature, and story text.

A blank value in your translation falls back to English in-game, so partial translations are welcome.
