# One More Game — Mods

Community mods for One More Game's titles. Right now that means **localization** for **SWAPMEAT**: help us
translate the game better than we did, or add a language we don't ship yet.

> This repository holds **mods**, not the game — translation text files and their manifests. There's no game
> code, art, or audio here. A mod is reference-only: it changes text the game already has; it never adds new
> content or code.

## Use a language mod (no account, no internet needed)

1. Download a pack — click **Code → Download ZIP**, or grab the three files for one language from
   [`swapmeat/localization/official/`](swapmeat/localization/official/) (a `.mod.json` and its two `.csv`s).
2. Drop them in the game's `mods/` folder:
   - **macOS:** `~/Library/Application Support/OneMoreGame/SWAPMEAT/mods/`
   - **Windows:** `%USERPROFILE%\AppData\LocalLow\OneMoreGame\SWAPMEAT\mods\`
3. Launch SWAPMEAT and pick the language in **Options** — a modded language shows `[MOD]` next to its name.

That's the whole thing. It works offline, off-Workshop — the files just have to be in the folder.

## Improve a language, or add your own

We want your help. See **[CONTRIBUTING.md](CONTRIBUTING.md)** — fork, edit a CSV, open a pull request. Our
checks run automatically and tell you if anything's off; a maintainer merges when it's green.

- **Improve an existing language** — edit its file under
  [`official/`](swapmeat/localization/official/) (e.g. `omg-zh-Hans.UIStrings.csv`).
- **Add a new language** — start from the English source in
  [`_reference/`](swapmeat/localization/_reference/) and create a pack under
  [`community/`](swapmeat/localization/community/).

## What's here

```
swapmeat/localization/
  official/     — the languages One More Game ships (this is the real, shipping text — edit to improve)
  community/    — languages and alternate translations authored by players
  _reference/   — English source strings, to translate a new language from
  glossary.csv  — established translations of names and key terms (the checks read this)
```

Everything here is safe to share and free to use for making and playing SWAPMEAT mods. See
[LICENSE](LICENSE).
