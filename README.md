# BUSN31230-Data-Viz-Final-Project

This dashboard is designed for baseball fans and analysts who follow the game casually or seriously. The story it shows is for people who have strong opinions about how baseball has changed, but haven't examined the underlying data.

The project set out to put data behind conventional baseball wisdom like "the game's gone soft" or "too many strikeouts and not enough hits." To prove or disprove these sayings, I set out to answer four central questions:
* How have strikeouts per game changed across eras? Did home runs rise as batting average declined over eras, and does the data support the more modern "Three True Outcomes" narrative? (https://www.mlb.com/glossary/idioms/three-true-outcomes)
* Does striking out more actually hurt a team's ability to score runs, and has that changed over time? Do high-strikeout teams win more games?
* Do offense and pitching move together across eras, or does one side gain a sustained advantage?
* Is there a relationship that fan attendance follows, and did it break down in the modern era with the declining attendance numbers?


Data Source
All of the data used comes from the Lahman Baseball Database, which is one of the most comprehensive publicly available sports datasets. I accessed and pulled from it using the pybaseball Python library (lahman.teams_core()), pulling from the cbwinslow/baseballdatabank GitHub repository. The dataset covers all MLB teams (AL and NL) from 1980 to 2021 with a total of 42 seasons, 30 teams, and approximately 1,200 team-season records.


Data Cleaning & Preparation
The raw Teams table was filtered to 1980–2021, AL and NL only. All rate statistics (runs per game, SO per game, HR per game, batting average, ERA) were calculated from raw counting stats to ensure consistency. For the Three True Outcomes Index chart, HR per game, BB per game, and batting average were normalized to a baseline of 100 in 1980, so all three metrics could be compared on the same axis (the trend, not the normalized values). An era label field was added to categorize seasons into six broadly recognized periods (Early Modern, Steroid Era, Steroid Era Peak, Pitching Dominance, Three True Outcomes, and the Modern Era). The cleaned data was exported to Excel, downloaded, and connected to Tableau.


Assumptions & Limitations
* ERA is used as a value to quantify a pitcher's quality. It is an imperfect measure since it depends on the external scorer's judgment about errors.
* The dataset ends at 2021. The 2023 rule changes (pitch clock, shift ban) are not reflected, and could be worth analyzing in a future version.
* The 2020 COVID season (60 games compared to the usual 160+ games) introduces noise into attendance and some rate stats.
* The ERA vs. Runs Per Game chart has an inherent relationship since ERA is derived partly from earned runs. The chart is most useful for showing how stable the ratio between ERA and total runs has been across eras, not for showing independence between the variables.
* Era boundaries are approximate and not universally agreed upon. I found them from online sources I read, and they represent reasonable turning points based on commonly cited baseball history.


Use of AI (ChatGPT and Claude):
My original plan was to use the MLB Stats API and pybaseball's FanGraphs functions (which I have used before), but both failed. The API didn't return anything but errors, and FanGraphs blocked all pybaseball requests with 403 errors. Claude said the Lahman database was a great alternative, and ChatGPT wrote the Python code to access it, but it found several errors, like renamed functions and columns, so it suggested I download the CSV directly from GitHub as a workaround.
Design Decisions
The project was originally focused on hockey trends across multiple leagues and putting numbers behind hockey sayings. The hockey analysis was abandoned because bulk data collection was infeasible. Hockey-Reference only covers the NHL (not other leagues), and EliteProspects requires business API access. I pivoted to Baseball because the Lahman database provides clean, free, and complete data. The dashboard was designed so that every chart could stand alone without much narration. Each title is written as a finding rather than a label, key moments are annotated directly on the charts, and the Era and Team Name filters let viewers explore for themselves interactively.
