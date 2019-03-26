# LANL-Earthquake-Prediction
Submissions for the Kaggle competition found here: https://www.kaggle.com/c/LANL-Earthquake-Prediction

## Competition Description

Given a segment of an acoustic signal, one must predict the _'time\_to\_failure'_, or in other words, time before the next laboratory earthquake. The metric used for model evaluation is **Mean Absolute Error (MAE)**. 

### Note

I will update the repository with the best approach I have been able to come up with yet. The repo is live, and subject to change.

### Best Approach thus far:

I used Gradient Boosting after extracting several features from the input acoustic data.

**Data Engineering**: 
1. Split input signal into chunks of 150000 data points. This is done based on the information given by the competition organisers.
2. For each of these _segments_, several statistical features are calculated (can be viewed in the notebook).
3. The training data is a collection of these segments, 4194 of them, to be precise.
4. The data is then scaled using scikit-learn's ```StandardScaler()``` function.


Next, we use the ```GradientBoostingRegressor``` and train over the training data. The training is done using K-Fold cross validation, and for each fold, the estimator object (model) is saved. After examining the results, the best estimator is chosen to make the predictions on the testing data. I used the **huber** loss function as it is less prone to fluctuations and outlier values, and I feel in this case, it gives better approximations. 

#### Kaggle Score for Approach
I got **MAE=1.583** on the Public Leaderboard for this approach.