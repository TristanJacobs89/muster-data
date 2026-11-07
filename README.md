# muster-data

Rules text for [Muster](https://github.com/TristanJacobs89/muster), a Warhammer 40,000 list builder and battle tracker, written in Muster's own words.

## Branches

One branch per data version, named after the game-datacards data version it matches (`995`, `996`, ...). An older version stays available, so the app can fall back to it. `main` holds only what every version shares.

## Files

| Path | What it holds |
| --- | --- |
| `manifest.json` | The data version, Muster's release date for it, and `from` with the text keys whose source text changed, came or went since that version (points and units are in Muster's own data) |
| `text/<part>.json` | One map of text key to text per part: `core`, `missions`, `secondaries`, `detachments` and one file per faction |
| `data/` | Muster's faction keys and the pinned commits of the sources |
| `editorial/glossary.json` | The game terms the text keeps exact |
| `reports/` | Counts per data version: how many texts, of which kinds |

A text key names where the text belongs in Muster's game data, for example `necrons/datasheets/<id>/data/abilities/<name>/text`. The names, characteristics and points themselves are not here: Muster's app gets those from its own data bundles.

## How the text is made

Fixed formulas (unit composition, wargear options, transport capacity) come from the structured data. The rest is drafted by a model to Muster's style guide, checked automatically against its source, and reviewed by hand. The tooling lives in Muster's `packages/texts`.

This repository holds no Games Workshop text. Warhammer 40,000 is a trademark of Games Workshop; Muster is not affiliated with Games Workshop.
