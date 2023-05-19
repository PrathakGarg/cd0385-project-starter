# Report: Predict Bike Sharing Demand with AutoGluon Solution
#### NAME HERE

## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?
We recieved a training dataset and a testing dataset. Since we did not have the columns 'casual' and 'registered' in the testing dataset we couldn't use them for the training either so they were dropped. The evaluation metric we used was Root Mean Square Error

### What was the top ranked model that performed?
RandomForestMSE_BAG_L2 was the top ranked individual model. But overall WeightedEnsemble_L3, which is a weighted collection of all the models based on a metric, performed the best

## Exploratory data analysis and feature creation
### What did the exploratory analysis find and how did you add additional features?
On doing a preliminary EDA we found that our count data in heavily left skewed. Other than that we observe that we have categorical columns like 'holiday', 'season', 'working_day' and 'weather'. We added additional features by converting the formentioned columns to categories and splitting datetime column to year, month, day and hour

### How much better did your model preform after adding additional features and why do you think that is?
Our error score decreased from 1.788 to 0.66439. Thus, we can conclude that featuer extraction improved the model quite significantly.

## Hyper parameter tuning
### How much better did your model preform after trying different hyper parameters?
I first tried using different hyperparameter tuning presets like 'toy'. They were lighter so more models could be tested in the same amount of time but the score I got wasnt much improved. Then I added hyperparameter tuning using bayesian optimizer which improved the score to 0.46506

### If you were given more time with this dataset, where do you think you would spend more time?
I think the optimal aspect to spend more time would be feature extraction. I think more complex features can be extracted from this data that can drive good correlations with our count.

### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.
|model|time_limit|preset|additional_hp|score|
|--|--|--|--|--|
|initial|600|best_quality|default|1.788|
|add_features|600|best_quality|default|0.66439|
|hpo|600|best_quality|Bayes Optimizer HPO|0.46506|

### Create a line plot showing the top model score for the three (or more) training runs during the project.

![model_train_score.png](model_train_score.png)

### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.

![model_test_score.png](model_test_score.png)

## Summary
We observed how autogluon can save our time spent in testing various types of models and we can focus on spending more time on data preprocessing and hyperparameter tuning get decent results in very little time
