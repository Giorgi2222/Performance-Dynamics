# Player Performance Dynamics Analysis
## Overview
Over the past few years, Dinamo Batumi, my local football (soccer) club, has been signing talented players who are on the decline, in the hopes of reviving their careers and acquiring higher-level players at a lower cost. Unfortunately, none of these deals have been successful, but the management has continued with this tactic, attributing any failures to bad luck rather than a flawed approach.<br />
In this project, I aim to investigate whether football (soccer) players who experience a decline in their performances are able to recover and return to their past level or if they usually continue to decline.
## Data
To conduct an analysis of players' performances, I used data from "Transfermarkt," which is a widely recognized and reputable platform for player evaluation. This platform aggregates data from hundreds of leagues worldwide and uses it to calculate the market value of individual players.
## Preprocess 
From a large dataset, I extracted data for players who had available data for five consecutive years. However, before dividing the data into features and labels, I needed to account for the age factor in market values. In football, even if a player's performance does not decline, their market value can decrease, and this decline is often irreversible. Therefore, using raw market value data could introduce bias towards the irreversibility of transfer value decline. To address this issue, I opted to use percentile rankings, which represent how a footballer's market value compares to other players of the same age, instead of using their market values directly.<br />
Finally, after obtaining the percentile rankings, I split the five-year data for each player into features (the first four years) and labels (the fifth year). The features are used to make predictions for the next year, while the labels are used to evaluate the accuracy of the model.
## Statistics
From the percentile ranking data, we can see that only 38% of players whose ranking has decreased for three consecutive years show any increase in their ranking on the fourth year.
## Modeling
While we already can draw conclusions from the statistics above, we can also use machine learning to predict the most likely outcomes for individual players. For this task, I have selected the LSTM network as the model because of its ability to capture dependencies and patterns in sequences, which makes it particularly suitable for this type of prediction. By using the players' ranking data from the last four years, the model will derive the best parameters to predict their most likely ranking in the future.
Based on statistics above, we can already make a conclusion, but we will try to predict most likely outcomes for individual players. To do that, we need a machine learning model. I chose the LSTM network as the model for predicting future performances because of its ability to capture dependencies and patterns in a sequence, making it the most suitable option for this particular task. Based on last four years' ranking, it will derive the best parameters to predict players most likely ranking in the future. 
## Results
Once our model was trained, I utilized it to predict the performances of failed players in Dinamo Batumi, based on their dynamics in the four years preceding their arrival at the club. By doing so, we aimed to determine whether their failure was a result of bad luck, or whether it was naive to expect them to regain their past level of performance in the first place.
<pre>
Godfrey Oboabona<br />
Last four years:  79.39946416, 71.66619975, 70.09111617, 43.49641009<br />
Prediction for the season with Dinamo Batumi:            37.81698<br />

Abraham Frimpong<br />
Last four years:  79.39946416, 44.95377504, 40.44419134, 36.1245617<br />
Prediction for the season with Dinamo Batumi:            33.233208<br />

Lukas Grozurek<br />
Last four years:  27.77559956, 40.00560303, 51.42748671, 29.08665887<br />
Prediction for the season with Dinamo Batumi:            26.693398<br />
</pre>
## Conclusion
As we observe, the predicted performance level in each case does not only not return to its highest levels, but rather continues to decrease even when compared to the previous year. Therefore, at the time of their transfer, it would be logical to expect these players to continue their decline in performance. <br />
Regrettably, the same holds true for Dinamo Batumi's latest transfer, Moussa Konaté. While I certainly hope that he regains his form and becomes a valuable asset to our club, the data suggests that the chances of that happening are very slim.
<pre>
Moussa Konaté<br />
Last four years:  90.88457767, 84.22551253, 75.75972616, 60.63432836<br />
Prediction for the season with Dinamo Batumi:            56.75379759<br />
</pre>

## Dependencies
- pandas
- numpy
- scipy
- scikit-learn
- keras

You can install these dependencies using pip by running:
<pre>
pip install pandas numpy scipy scikit-learn keras
</pre>

## Usage
1. Make sure all the required libraries are installed.
2. Download the 'player_valuations.csv' and 'birth_years.csv' files.
3. Open Jupyter notebook and run 'Player Performance Dynamics Analysis.ipynb'.

