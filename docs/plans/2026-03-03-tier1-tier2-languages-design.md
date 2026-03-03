# Tier 1/2 Bidirectional Languages Only

## Context

The TranslateGemma technical report (arxiv 2601.09012) includes MetricX benchmark scores for the 4B model. We are updating the app to support only the bidirectional languages that score well (tiers 1 and 2), plus Japanese by explicit request.

## Language Set (12 total, all bidirectional)

| Language | Code | Tier | GT 4B MetricX |
|---|---|---|---|
| English | en | — | — |
| Chinese | zh-CN | 1 | 2.66 |
| Dutch | nl | 1 | 2.84 |
| French | fr | 1 | 2.97 |
| German | de | 1 | 1.93 |
| Indonesian | id | 1 | 2.63 |
| Japanese | ja | explicit | 4.44 |
| Korean | ko | 2 | 3.93 |
| Russian | ru | 2 | 3.25 |
| Spanish | es | 1 | 2.51 |
| Thai | th | 2 | 3.49 |
| Vietnamese | vi | 1 | 2.87 |

## Removed Languages

Cantonese (yue), Chuukese (chk), Ilocano (ilo), Marshallese (mh), Tonga (to), Filipino (fil), Hawaiian (haw), Samoan (sm).

## Changes

### Data model

- `LANGUAGES: dict[str, tuple[str, bool]]` → `LANGUAGES: dict[str, str]` (name → BCP-47 code)
- Delete `_build_target_langs()` and `TARGET_LANGS`
- `SOURCE_LANGS` = sorted list of all 12 languages

### UI

- Derive valid targets inline: English targets all others sorted; others target English
- Swap button always enabled — remove `can_swap` logic
- Defaults unchanged: source=English, target=Spanish

### Tests

- `LANGUAGES` count: 15 → 12
- Values are `str` not `tuple` — update type assertions
- Remove unidirectional tests
- `SOURCE_LANGS` count: 12 (all languages)
- English targets: 14 → 11
- Update BCP-47 code checks for new language set
- Remove or adapt `TARGET_LANGS`-related tests

### CLAUDE.md

- Replace bidirectional/unidirectional language lists with single list
- Remove mention of swap button disabled state

### No changes

Model loading, translation logic, prompt template, performance output, known issues.
