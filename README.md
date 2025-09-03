# nhl-machine-learning
This is a data science project, exploring NHL data through machine learning techniques. This projects collects, cleans and analyzes nhl historical team data to build a predictive model with the aim of predicting if a given team will win or lose against another one. It includes data preprocessing, feature engineering, training, evaluation.

## Features
 
**Data Scraping** | **Python, requests, BeautifulSoup**

Data is scraped from Hockey Refrence (www.hockey-refrence.com) by extracting the relevant tables from the HTML using BeautifulSoup.

All the games played in the NHL from the 2000-2001 season all the way up to the 2024-2025 season are extracted.
  
**Data Cleaning** | **Python, pandas**

The data is cleaned by removing unwanted rows, and fixing the outdated data.

For example, the rows that are copies of the header are removed, and the Arizona Coyotes' (ARI) data is renamed to the Utah Mammoth (UTA), since the name of the organization changed.
  
**Data Preprocessing** | **Python, pandas**

The data is turned into integer values and values that are usable by machine learning models:
- location_code: 1 for away, 0 for home.
- team_code: unique int value based on team.
- opp_code: unique int value based on opposition team.
- ot_code: 1 for games that were decided in overtime/shoutouts, 0 for games that were decided in regular time.
- target: 1 for win, 0 for loss.
Other match data is also transformed to values that can be used by machine learning models:
- gf: Goals For (number of goals the team scored in that game).
- ga: Goals Against (number of goals the opponent scored).
- sog: Shots on Goal (shots directed at the net).
- pim: Penalty Minutes (total minutes spent in the penalty box by the team).
- ppg: Power Play Goals (goals scored while the team had a man advantage).
- ppo: Power Play Opportunities (number of scoring chances the team had on the power play).
- shg: Short-Handed Goals (goals scored while the team was down a man due to a penalty).
- fow: Faceoffs Won (number of faceoffs the team won).
- fol: Faceoffs Lost (number of faceoffs the team lost).

**Training Machine Learning Model** | **Python, pandas, sklearn**

Random Forest Classifier from Sklearn is used to build the machine learning model:
- The training data is all the games in our dataset before 2024-10-04 (All seasons from the 2000-2001 season to the 2023-2024 season)
- The testing data is all the games in the 2024-2025 season
- The predictors are the team, the opposition team, whether the team is playing back to back games, whether the opposition team is playing back to back games, and match statistics from the previous 6 games.
- The predicted is whether a team will win or lose.

When a team is predicted to win and the opposing team is predicted to lose for a same game (when both perspective align for a given game), the model is correct **62.47%** of the time.

## Future improvements:
- Use player/roster/injury data to improve accuracy.
- Predict overtime wins/loses too, not only wins and losses.
- Add real predictions using the trained model.

## Setup
Made using Google Collab.

## Credit
All data is scraped from Hockey Refrence: www.hockey-reference.com.
Inspired by Dataquest Football data scraping and predicting.
