# udacity_aws_mle_prj-1
Udacity's first project of the AWS Machine Learning Engineer nanodegree. AutoGloun was used to create an AutoML regression model to predict bikeshare demand, given a set of independent variables. The dataset used is available in Kaggle at the following [link](https://www.kaggle.com/c/bike-sharing-demand/overview). The head of the dataset is shown below:
![head.PNG](/img/head.PNG)
## Initial Training
- The predicted values of the bike sharing demand had to be greater than or equal to zero. Therefore, the output dataframe had to be checked if it included negative values. However, in the three cases, there were no negative values in the prediction dataframe.
- The score of the top ranked model was 1.80851.

## Exploratory data analysis and feature creation
The exploratory data analysis showed that there were no issues with the dataset, and that most of the continuous variables were normally distributed. However the categorical data were set to category type, and encoded using One Hot Encoder. The year, month, day, and hour were extracted from the date column, and were also used as predictors. Another feature was added which was humidity times temperature. 

### Reults of feature engineering
The model performed significantly better than the previous model, at a score of 0.48979. That is because the model was able to identify categorical variables, given that their type was changed to category, and that they were encoded. Using the datetime components as predictors must have also contributed to the improvement of the model. Additionally, to account for the high temperature but low humidity levels, and vice versa, an additional feature was added by multiplying the two features. 

## Hyper parameter tuning
### Results of HPO (Hyperparameter Optimization)
The model's performance slightly decreased by a fraction, to be 0.50712.
### Recommendations
I would spend more time with both feature engineering, and internal hyperparameters tuning. I would also focus on optimizing the top performing models, like CatBoost.

### The following table summarizes the results.
|model|auto_stack|num_stack_levels|num_bag_folds|score|
|--|--|--|--|--|
|initial|False|0|0|1.80851|
|add_features|False|0|0|0.48979|
|hpo|True|3|10|0.50712|
