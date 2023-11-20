# F1-race-winner-prediction-2018-season---Machine-learning-project

## Project Description: 
As a life-long Formula 1 fan, before the races I always took a shot at who was going to be the winner just for fun. Considering all the variables that I could think of. This project combines my life-long passion with the new knowledge that I have acquired, ending up in a perfect combination for learning with passion, drive and having the strength and interest to solve the challenges that arise.

This project intends to predict the winner of each F1 race for the 2018 season, a season with several unexpected winners that can be a real challenge to get right. However, the project can be implemented to whichever F1 season, just changing the season variable in the code.

For the machine learning models, Algorithms included in the scikit-learn library are implemented and tested. The data used was collected from http://ergast.com/mrd/, with data available since the 1950 season. This data includes information about race results, qualifying results, circuits, constructors, drivers, standings, breakdowns, and driver mistakes.

Building this project came with some extra challenges: dealing with an imbalance data set (the number of non-winners is much larger than the number of winners), avoiding data leakage while doing the feature engineering, getting a concrete winner prediction for each race of each year, computing power required for working with a non-small dataset using sklearn.

## EDA
Being familiarized with the world of Fomula 1 has endowed me with the knowledge necessary to spot and correct errors in the data. Besides that, it makes it easier to know where to look for meaningful insights.

Different datasets are combined and cleaned to get just one dataset with the useful considered useful. Some meaningful insights:
1. The constructors who compete in the latest seasons of F1 show a lower DNF ratio due to constructor fault or breakdown, being more reliable and using less of the same components as construcotrs that competed in previous seasons. This fits perfectly the new sustainable direction that Formula 1 has been pushing for, starting in 2006 and evolving throuhg the years with meaningful and important changes in 2014.
2. The drivers that have been World Champions are less prone to crash, showing that a "Formula 1 season is a marathon, not a sprint", being consistency a key factor to achieve success.
3. The World Champions are rain masters! World Champions such as Ayrton Senna, Lewis Hamilton, Michael Schumacher, Max Verstappen, Jeson Button excel under the rain. This manifests a great ability to perform better than others when the conditions on track are far from ideal, when the decisions must be made quicker than usual and the feel for the changing conditions gets rewarded.

Several features as DNF rate for constructor and driver are engineered and transformations are aplied to avoid data leakage, the metrics for DNF rate are obtained per season for constructor and driver, and are moved to the following season, thus avoiding data leakage. The feature "Points" presents a similar challenge, the tally of points is moved to the following race for each driver, as is reckoned that this is information that will not be available once the model is deployed.

## Machine Learning
The problem of predicting a winner is approached as a classification problem, a range of models are selected bases on their suitability to the problem. Linear models and tree-based models are selected, the later considering their suitability to dealing with imbalanced classes.

The following models were considered: Logistic Regression, K-nearest neighbors, SVC, Random Forest, Gradient Boosting Decision Trees and Neural Networks. For evaluating these models different metrics such as: recall, precision score and f1 score were taking into account, given that accuracy is not sufficient on its own to evaluate an imbalance class problem as the one presented here (a simple base line algorithm could simply predict the most common class and get a high accuracy).

To prepare the data for the training process, it was necessary to do an over sample to avoid losing information and later a scaling of the data for the algorithms that required it.

It was necessary to create a custom scoring function to get a predicted winner for each race of the season. The model was set to provide the probability of winning for each driver, being the predicted winner the one with the highest probability.

## Findings
As expected, the tree-based models were among the best performers together with the neural network. The SVC models were the most difficult to fine-tune due to the computing power they required to be trained in the dataset used.

Surprisingly, the weather features play no role in the prediction of the winner. The most important features are "Grid Position" and "Points", showing how difficult it is to overtake in nowadays Formula 1 despite the introduction of DRS in 2011 and the importance of the performance of the pair driver-car for getting a shot at winning. The reliability of constructors and drivers plays a part in the prediction as well and it is equally noticeable that the most succesful drivers have a higher chance of winning despite having subpar machinery at their disposal.

A first iteration was made, considering the weather data but no the points score by the drivers in the season. In the second iteration, the points scored by the drivers in the season were considered and the weather data was dropped off, considering that it had no effect on the first iteration according to the features importance. The changes led to an increase in the score of 5%.

The three best models: Random Forest, Gradient Boosting Decision Trees and Neural Network were also tested on the 2017 and 2019 seasons, getting acceptable results considering that were not specifically fine tune for these seasons.

The best results on the target season, the 2018 season were obtained from Random Forest and Neural Network models, predicting the winner correctly 62% of the races (13/21). This is considered a great result, considering the unpredictability of the sport, with factors such as: disqualifications, red flags, weather conditions, safety cars, tire performance and degradation, bad pip stops and human performance that can affect the drivers, mechanics, and engineers. Most of the times, even on the weekend of the race, the teams do not even know themselves where they are going to end up in the race.

This application can be useful in the betting industry, getting the winner right most times than not, we are in for a potentially good profit.

## How can it be better?
The computing power was a limitation for fine tuning the models, the free cloud services do not offer sessions long enough to properly fine-tune the most demanding models such as SVC.

Another improvement area is the unavailability of data that can dramatically change the outcome of a race, like red flags, and safety cars. Getting this data could improve the results obtained.

With a bit more time, the engineering of more features could be done, what could potentially lead to getting better results.
