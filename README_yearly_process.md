## 2025 model runs

#### Files of importance:
- yearly_model_runs.ipynb is where you make your predictions
- model_creation.ipynb is where you can remake your models if needed (shouldn't have too but good to know)

#### Steps after completing model runs
1. (15 minutes) Download csvs from baseball savant with respective columns in the batter and pitcher prediction cells below. There will be three datasets to collect: batters (min 200 PAs), starters only (min 450PAs or 100 IPs), and relievers only (min 100PAs or 25IPs).
- Batters Columns are: "last_name, first_name","player_id","year",'k_percent', 'bb_percent', 'exit_velocity_avg',
    'launch_angle_avg', 'sweet_spot_percent', 'barrel_batted_rate',
    'hard_hit_percent', 'avg_best_speed', 'avg_hyper_speed',
    'z_swing_percent', 'z_swing_miss_percent', 'oz_swing_percent',
    'oz_swing_miss_percent', 'oz_contact_percent', 'iz_contact_percent',
    'whiff_percent', 'swing_percent', 'pull_percent',
    'straightaway_percent', 'opposite_percent', 'groundballs_percent',
    'flyballss_percent','sprint_speed'
- Starting Pitchers Columns are: "last_name, first_name",player_id,year,p_formatted_ip,ab,exit_velocity_avg,launch_angle_avg,sweet_spot_percent,barrel_batted_rate,hard_hit_percent,z_swing_percent,z_swing_miss_percent,oz_swing_percent,oz_swing_miss_percent,oz_contact_percent,meatball_percent,iz_contact_percent,whiff_percent"
- Relief Pitchers Columns are: "last_name, first_name",player_id,year,p_formatted_ip,ab,exit_velocity_avg,launch_angle_avg,sweet_spot_percent,barrel_batted_rate,hard_hit_percent,z_swing_percent,z_swing_miss_percent,oz_swing_percent,oz_swing_miss_percent,oz_contact_percent,meatball_percent,iz_contact_percent,whiff_percent"
2. (1 minute) Load in the XGB models for batters and pitchers.
3. (10 minutes) Run the batters predictions using the batter model, then both sets of pitcher predictions using the pitcher model.
4. Get BABIP and 3yr BABIP for both hitters and pitchers from Fangraphs. Copy into two excel sheets and create a third sheet where you can VLOOKUP the two babip values to the singular player name. 
    - For Hitters: Use Min 200PA for BABIP and Min 500PA for 3yr BABIP. 
    - For Pitchers: User Min 30IP for BABIP and Min 80IP for 3yr BABIP
5. Create Copy of "fantasy_baseball_draft_guide.xlsx" file for your new year and begin the copy over process. You can do Step 8 below, or for a faster route, just copy and paste in this years values over last years and the values should populate themselves.
6. Grab all batters above 0.075, starters above 0.100, and relievers above 0.750 and append them in an Excel file (last year I did this manually). The reason I did this was so I knew that if a players name wasn't on the list, don't consider drafting him.
7. Get ADP and Position from Fangraphs at https://www.fangraphs.com/fantasy-tools/player-rater?pos=&posType=&sortcol=3&sortdir=asc and copy that only draft guide file.
8. Using VLOOKUP's (manual) or Joins (automatic, not implemented yet), Combine these in Excel and make a Table of:
- Name 
- Position
- great_season_probability, 
- ADP
- Round (aka Ceiling(ADP/12)), 
- BABIP_Expectation_Batter (aka calculate BABIP - BABIP 3yr, then say)
    - if over 0.01, "Regression"
    - if between -0.01 and 0.01, "Same"
    - if under -0.01, "Improve"
- BABIP_Expectation_Pitcher (aka calculate BABIP 3yr - BABIP, then say)
    - if over 0.01, "Regression"
    - if between -0.01 and 0.01, "Same"
    - if under -0.01, "Improve"
9. Sort by ADP, then conditional format the great_season_probability column from green (high) to white (low).
10. This table should give you all players worth considering drafting, sorted by ADP, and the probability they will have a great season.

Output should look like fantasy_baseball_draft_tool_2025.xlsx. Use the table from Rows 1-25 to make a draft plan based on your mock drafts and the players available around your draft position. Use Rows 31 and onward to make a searchable table of your draftable players. Note that by filtering by position through typing the position, you can get players with multiple positions as well.

#### Future improvements:
- Have an automated "Draft Plan" made based on draft position, number of teams in a league, and player position allotments per team. The great_season_probability value along with using ADP to find what players are around that position is what would be used to suggest the best pick, a backup #1, and backup #2 for each round
- Automate it where we can have both the draft plan and the searchable table out of excel and into a website page (html maybe, use LLM app to determine best method)