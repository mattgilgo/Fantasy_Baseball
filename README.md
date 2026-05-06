# Fantasy Baseball Projections

> XGBoost-powered player projections for fantasy baseball drafts, built on Baseball Savant Statcast data.

## Overview

This repo produces per-player "great season" probability scores for batters, starting pitchers, and relief pitchers using XGBoost regression models trained on Statcast metrics. Outputs feed a yearly Excel draft guide that pairs probabilities with ADP, BABIP regression signals, and positional filters — making it easy to spot value picks and avoid overpriced busts.

The system has been run annually since 2023 and is updated each spring before the draft.

## Features

- Separate XGBoost models for batters, starting pitchers, and relief pitchers
- Great-season probability score per player, scaled by position for relative comparison
- BABIP regression signals (batter and pitcher) to flag expected improvement or decline
- ADP integration from FanGraphs and FantasyPros for draft-slot value analysis
- Excel draft guide with conditional formatting, positional filters, and a round-by-round draft plan section

## 2026 Predictions

Use these CSVs directly for your draft:

| Player Type | File |
|---|---|
| Batters (min 200 PA) | [xgboost_great_season_rankings_min200PA.csv](savant_predictions/2026/batters/xgboost_great_season_rankings_min200PA.csv) |
| Starting Pitchers | [xgboost_great_season_rankings_only_starters.csv](savant_predictions/2026/pitchers/xgboost_great_season_rankings_only_starters.csv) |
| All Pitchers | [xgboost_great_season_rankings_starters_and_relievers.csv](savant_predictions/2026/pitchers/xgboost_great_season_rankings_starters_and_relievers.csv) |

The full draft tool (with ADP, BABIP signals, and a draft plan table) is at [yearly_draft_guides/fantasy_baseball_draft_tool_2026.xlsx](yearly_draft_guides/fantasy_baseball_draft_tool_2026.xlsx).

## How It Works

1. Download Statcast data from [Baseball Savant](https://baseballsavant.mlb.com/) for batters (min 200 PA), starters (min 100 IP), and relievers (min 25 IP)
2. Load the pre-trained XGBoost models from `models/` and run predictions in `yearly_model_runs.ipynb`
3. Pull BABIP and 3-year BABIP from FanGraphs; compute regression expectation per player
4. Pull ADP from FanGraphs or FantasyPros and combine with predictions in the draft tool Excel file
5. Sort by ADP, filter by position, and use the probability scores to find value relative to draft slot

See [README_yearly_process.md](README_yearly_process.md) for the detailed annual workflow.

## Key Stats Used

**Batters:** K%, BB%, exit velocity, launch angle, sweet spot%, barrel rate, hard-hit%, sprint speed, zone contact rates, pull/oppo%, groundball/flyball%

**Pitchers:** IP, exit velocity allowed, launch angle allowed, sweet spot% allowed, barrel rate allowed, hard-hit% allowed, zone swing/miss rates, whiff%, meatball%

## Model Performance

| Year | League | Format | Draft Pos | Finish |
|---|---|---|---|---|
| 2022 | Doubles & Dingers E5 (12-team) | H2H Category | 6th | — |
| 2022 | The We Back League (8-team) | H2H Points | 7th | — |
| 2022 | Shamrocks and Shenanigans (10-team) | Rotisserie | 7th | — |
| 2022 | Reddit League (10-team) | Rotisserie | Auction | — |

## Archived Predictions

Earlier seasons used linear regression models (ElasticNet, Lasso, Ridge) before the switch to XGBoost. Those projections are preserved in `archive/` for reference.

## License

GPL-3.0 — see [LICENSE](LICENSE)
