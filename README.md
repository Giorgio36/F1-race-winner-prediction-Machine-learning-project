# F1-race-winner-prediction-2018-season---Machine-learning-project

## Project Description: 
As a life-long Formula 1 fan, before the races I always took a shot at who was going to be the winner just for fun. Taking into account all the variables that I could think of. This project combines my life-long passion with the new knowledge that I have acquired, endind up in a perfect combination for learning with passion, drive and have the strength and interest to solve the challengues that arise.

This project intends to predict the winner of each F1 race for the 2018 season, a season with several unexpected winners that can be a real challenge to get right. However, the project can be implemented to whichever F1 season, just changing the season variable in the code.

For the machine learning models, Algorithms included in the scikit-learn library are implemented and tested. The data used was collected from from http://ergast.com/mrd/, with data available since the 1950 season. This data includes information about race results, qualifying results, circuits, constructors, drivers, standings, breakdowns and driver mistakes.

Building this project came with some extra challengues: dealing with an inbalance data set (the number of non-winners is much larger than the number of winners), avoiding data leakage while doing the feature engineering, getting a concrete winner prediction for each race of each year, computing power required for working with a non-smmall dataset using sklearn.

## EDA
Being familirized with the world of Fomula 1 has endowed me with the knowledge necesary to spot and correct errors in the data. Besides that, it makes it easier to know where to look for meaningful insights.

Different datasets are combined and cleaned to get just one dataset with the useful considered useful. Some meaningful insights:
1. The constructors who compete in the latest seasons of F1 show a lower DNF ratio due to constructor fault or breakdown, being more reliable and using less of the same components as construcotrs that competed in previous seasons. This fits perfectly the new susitanable direction that Formula 1 have been pushing for, starting in 2006 and evolving throuht the years with meaningful and important changes in 2014.
2. The drivers that have been World Champions are less prone to crash, showing that a "Formula 1 season is a marathon, not a sprint", being consitency a key factor to achieve success.
3. The World Champions are rain masters! Wordl Champioins such as Ayrton Senna, Lewis Hamilton, Michael Schumacher, Max Verstappen, Jeson Button excel under the rain. This manifest a great ability to perform better than others when the conditions on track are far from ideal, when the decisions have to be made quicker than usual and the feel for the changing conditions gets rewarded.

Several features as DNF rate for constructor and driver are engineered and transformations are apllied to avoid data leakage, the metrics for DNF rate are obtained per seson for constructor and driver, and are moved to the following season, thus avoiding data leakage. The feature "Points" presents a simmilar challenge, the tally of poinst is moved to the following race for each driver, as is reckoned that this is information that will not be available once the model is deployed.

## Machine Learning
The problem of predicting a winner is approached as a classification problem, a range of models are selected bases on its suitability to the problem. Linear models and tree based models are selected, the laters taking into account theit suitability to dealing with imbalanced classes.

The following models were taken into account: Logistic Regression, K-nearest neighbors, SVC, Random Forest, Grandient Boosting Decision Trees and Neural Networks. For evaluating these models different matrics such as: recall, precision score and f1 score were taking into account, given that accuracy is not sufficient of its own to evaluate an inbalance class problem as the one presented here.

To prepared the data for training process, it was necessary to do an over sample to avoid losing information and later an scaling of the data for the algorithms that required it.

## Findings
As expeected, the tree based model were among the best performers together with the neural network. The SVC models were the most difficult to fine tune due to the computing power they required to be train in the dataset used.

Surprisingly, the weather features play no role in the prediction of the winner. The most important features are "Grid Position" and "Points", showing how difficult it is to overtake in nowadays Formula 1 despite the introduction of DRS in 2011 and the importance of the perfomance of the pair driver-car for getting a shot at winning. The reliability of constructors and drivers plays part in the prediction as well and it is equally noticeable that the most succesful drivers have a higher chanche of winning despite having subpar-machinery at their disposal.

A firrst iteration was made, considering the weather data but no the points score by the drivers in the season. In the second iteration, the points scored by the drivers in the season were taken into account and the weather data was drop off, considering that it had no effect on the first iteration according to the features importances. The changes led to a increase in the score by 5%.

The three best models: Random Forest, Gradient Boosting Decsion Trees and Neural Network were also tested on the 2017 and 2019 seasons, getting acceptable results taking into account that were not specifically fine tune for these seasons.

The best resulst on the target season, the 2018 were obtained from Random Forest and Neural Network models, predicting the winner correctly 62% of the races (13/21). This is considered a great result, considering the unpredictability of the sport, with factors such as: desqualifications, red flags, weather conditions, safety cars, tyre performance and degradation, bad pip stops and human performance that can affect the drivers, mechanics and engineers. Most of the times, even on the weekend of the race, the teams do not even know themselves were they are going to end up in the race.

This application can be useful in the betting industry, getting the winner right most times than not, we are in for a potentially good profit.

## How can it be better?
The computing power was a limitation for fine tuning the models, the free cloud services do not offered sesions long enough to properly fine tune the most demandind models such as SVC.

Another improvemetnt area is unavailability of data that can dramatically change the outcome of a race, as red flags and safety cars. Getting this data could improve the resuts obtained.

With a bit more time, the engineering of more features could be done, what could potentially lead to getting better results.
