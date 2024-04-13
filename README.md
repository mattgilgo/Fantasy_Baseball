# Fantasy_Baseball
This repo highlights my first stab at developing models to predict fantasy baseball performance by individual players.

## My Approach
Fantasy baseball statistics are split between two types of players, the "Batter" and the "Pitcher". Within the "Pitcher" player type, there are different stat targets for the "Starting Pitcher" and "Relief Pitcher". Three seperate datasets were needed for these, which were mostly derived from the fangraphs.com historical database. A litany of data was used to give a vast data profile of each player. Once the data was downloaded, the workflow went as followed.

1. Data Preprocessing - data cleanup, filtering, handling n/a values
2. Data Labeling - labeling each player by primary position (1B, SP, etc.)
3. Data Exploration - understanding stat and fantasy point production by position
4. Splitting datasets by position
5. Running multiple regression models against each position vs important batter/pitcher target stats
6. Identifying important features and highest performing models for each position
7. Making predictions based on highest performing regression model for each position
8. Scaling predictions by position to understand player tiers and draft slot positioning
9. Publish rankings by position and overall batter and pitcher rankings
10. Draft Away!

## Choose from these Predictions for your Fantasy Draft!
* Choose from the csvs below to view ranked projection for your fantasy baseball draft:
    - For Shallower Leagues (8,10) - (https://github.com/mattgilgo/Fantasy_Baseball/blob/main/savant_predictions/2024/final/overall_rankings_w_adp.csv)
    - For Deeper Leagues - (https://github.com/mattgilgo/Fantasy_Baseball/blob/main/savant_predictions/2024/final/overall_rankings_w_adp_min100PA.csv)

Archived:
* Projections using top performing model/position pairing for each position:
    - Batters - (https://github.com/mattgilgo/Fantasy_Baseball/blob/main/projections/batters/2023_scaled_overall_rankings.csv)
    - Starting Pitchers - (https://github.com/mattgilgo/Fantasy_Baseball/blob/main/projections/pitchers/starters/2023_ovr_sp_rankings_20230329-163907.csv)
    - Relief Pitchers - (https://github.com/mattgilgo/Fantasy_Baseball/blob/main/projections/pitchers/relievers/2023_ovr_rp_rankings_20230313-124854.csv)


## Model Performance Tracker
### Team Results
2022 Performance for teams drafted using these models:

| League                    | #Teams/League | Scoring Style | Draft Position | Total Points  | League Finish |
| ------------------------- | ------------- | ------------- | -------------- | ------------- | ------------- |
| Doubles & Dingers E5      | 12            | H2H Category  | 6th            | TBD           | TBD           |
| The We Back League        | 8             | H2H Points    | 7th            | TBD           | TBD           |
| Shamrocks and Shenangians | 10            | Rotisserie    | 7th            | TBD           | TBD           |
| Reddit League             | 10            | Rotisserie    | Auction        | TBD           | TBD           |
