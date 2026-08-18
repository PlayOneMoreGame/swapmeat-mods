# English source (`_reference/`)

The English strings to translate a **new** language from. Each file is `Key, Id, English(en)` — copy it,
rename to your language (`<yourname>-<locale>.UIStrings.csv`), replace the English value column with your
translation, and put it in [`../community/`](../community/). See [CONTRIBUTING](../../../CONTRIBUTING.md).

> To *improve* a language One More Game already ships, you don't need these — edit the existing pack in
> [`../official/`](../official/) instead.

**Not yet populated.** These CSVs are exported from the game's English string tables (they aren't the same
as the shipped translation packs, which are target-language-only). One More Game will add
`en.UIStrings.csv` and `en.GeneratedStrings.csv` here from the current build. Until then, new-language
authoring starts by copying an existing pack in `../official/` and retranslating.
