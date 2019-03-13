# LANL-Earthquake-Prediction
Submissions for the Kaggle competition found here: https://www.kaggle.com/c/LANL-Earthquake-Prediction

## Competition Description

Given a segment of an acoustic signal, one must predict the _'time\_to\_failure'_, or in other words, time before the next laboratory earthquake. The metric used for model evaluation is **Mean Absolute Error (MAE)**. 

### Approach 1:

We used Gradient Boosting after extracting very basic features from the input acoustic data.

**Data Engineering**: 
1. Split input signal into chunks of 150000 data points. This is done based on the information given by the competition organisers.
2. For each of these _segments_, the mean, standard deviation, maximum and minimum values are calculated.
3. The training data is a collection of these segments, 4194 of them, to be precise.
4. The data is then scaled using scikit-learn's ```StandardScaler()``` function.


Next, we use the ```GradientBoostingRegressor``` and train over the training data. 

Since the aim of this approach was just to create a baseline model, and set up the pipeline, we did not carry out any validation and instead verified using the entire training data itself, for which we got **MAE = 2.00975**.

#### Kaggle Score for Approach
We got **MAE=1.800** on the Public Leaderboard for this approach.

### Approach 2

The difference here is in the way features have been extracted, as well as the carrying out of K-Fold cross validation. Further, the notebook contains several data visualisations.

#### Kaggle Score for Approach
We got **MAE=1.999** on the Public Leaderboard for this approach.