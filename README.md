<p align="center">
  <img src="https://github.com/aothree/NBA-over-unders/blob/main/images/basketball%20photo.jpg"/>
</p>

# NBA-over-unders

Every year, Vegas books publish their win-totals and people can bet the 'over' or the 'under' depending on how they feel about a team going into the season.  For example, the Lakers win-total before the 2021-22 season was 52.5.  If you bet the over, the Lakers would need to win more than 52 games for you to win.  Likewise, betting the under would only win if they won under 53 games.  

The goal of this project is to build a classification model that can predict 'over' or 'under' on NBA season win-totals.  We will run and tune various models and pick the best model.  To be a viable model, it must beat the baseline accuracy of 51%.  

## Data

1. Scraped 20 seasons of over-under data from https://www.sportsoddshistory.com and organized in a dataframe.  

2. Scraped 20 seasons of advanced statistics from https://www.basketball-reference.com and organized in a dataframe.  

3. Cleaned and merged the data.  

## Modeling 

1. Our target to predict is `result`.  1 = Over, 0 = Under.  

2. Feature Engineering.  Investigated coefficients and created a few features that showed stronger correlations to our target.

3. Logistic Regression.  Accuracy score of 57.7%

4. Random Forest.  Tuned with GridSearchCV.  Accuracy score of 63.3%

## Conclusions 

The best model was Random Forest, with the following hyperparemeters:

`{'max_depth': 7, 'max_features': 7, 'min_samples_split': 3, 'n_estimators': 30}`
  
With a 63.3% Accuracy, we were able to beat the baseline model of 51.1% by over 12%.  Even when accounting for the vig (the cut charged by a sportsbook), you would turn a profit betting NBA over-unders using this model.  

When considering which over-unders to bet, it might be beneficial to consider the following stat:
In the last twenty seasons:

* Unders hit at a 60% rate for teams with predicted win totals >= 53
* Overs hit at a 60% rate for teams with predicted win totals <= 25
