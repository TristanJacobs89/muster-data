# muster-data

Game data and rules text for [Muster](https://github.com/TristanJacobs89/muster), a Warhammer 40,000 list builder and battle tracker: the data its bundles are packed from, and the rules text in Muster's own words.

## Branches

One branch per release, named after its data version (`972`, `981`, `995`; the game-datacards data version it was first made from). Muster's pipeline packs each release's bundle at the commit Muster pins (`packages/pipeline/data/muster-data.json`). A published release is frozen: its data must pack to the bundle id in its `release.json`, so a data change is a new release; its text may still change. `main` holds only what every release shares.

## Files

| Path | What it holds |
| --- | --- |
| `release.json` | The release: data version, bundle format, upstream commit and date (provenance), its factions, and the bundle id it was published as |
| `factions/<key>/data.json` | One faction's game data as its bundle file holds it: datasheets, points, wargear, detachments, enhancements, stratagems, army rules, with every rules text field empty |
| `shared/` | The core stratagems and keyword rules, the secondary deck, the Mission Deck, the battle sizes, and the JSON Schema of the bundle files |
| `manifest.json` | The data version, Muster's release date for it, and `from` with the text keys whose source text changed, came or went since that version (points and units are in Muster's own data) |
| `text/<part>.json` | One map of text key to text per part: `core`, `missions`, `secondaries`, `detachments` and one file per faction |
| `data/` | Muster's faction keys and the pinned commits of the sources |
| `editorial/glossary.json` | The game terms the text keeps exact |
| `reports/` | Counts per data version: how many texts, of which kinds; `coverage-<bundle>.json`, how much of a bundle's rules text Muster's own text covers (every text the source fills and every army rule); `baseline-published-<date>.json`, the bundles Muster published before muster-data became the source |

A text key names where the text belongs in Muster's game data, for example `necrons/datasheets/<id>/data/abilities/<name>/text`. Names, characteristics and points are in the data files; the text never is.

## How the text is made

Fixed formulas (unit composition, wargear options, transport capacity) come from the structured data. The rest is drafted by a model to Muster's style guide, checked automatically against its source, and reviewed by hand. The tooling lives in Muster's `packages/texts`.

This repository holds no Games Workshop text. Warhammer 40,000 is a trademark of Games Workshop; Muster is not affiliated with Games Workshop.
