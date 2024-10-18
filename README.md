# Selecting the right Classification Model

We are looking at a banking dataset for a Portuguese Bank to see if marketing campaigns would lead to a customer agreeing to open a Term Deposit. We would like to know what Classification Model would work best for this purpose.

We are looking a quite unbalanced dataset where there are very few records with positive classe compared to the negative class.

![App Screenshot](/images/unbalanced.png)

As an inital discovery action, we try to see if there are any relationships that pop out that might lead to a positive response. One of the relationship we tried to see is if having a certain type of job led to a higher positive repsonse.

![App Screenshot](/images/huntingRelation.png)

We failed to see any direct relationship between any specific attribute that led to a positive response.

### Preparing the data for modelling

There are quite a few columns in the data set and seeing that none really had a clear relationship to a positive response, to reduce the number of columns we decided to remove these columns -

1. job
2. month
3. day_of_week
4. pdays
5. default

There were some "unknown" values in columns 'loan' and 'housing'. Instead of trying to fill the unknowns with any values we decided to remove those rows as the count wasn't that high.

The categorial columns were then encoded so that they were numerical using OneHotEncoder or LabelEncoder.

### Modelling

Some of the Models we looked at are

1. Logistic Regression
2. KNN (K Nearest Neighbor)
3. Decision Tree
4. SVC (Support Vector Classifier)

Without knowing which model would work for this dataset we fit each model with the training dataset to see if any one of them performed better than the other. We ran a GridSearchCV for each model with different parameters to see get the best possible parameter that worked for each model and did a comparison againt other models and their ideal parameters.

![App Screenshot](/images/modelComparison.png)

![App Screenshot](/images/modelComparisonChart.png)

Looking at the results we see that all models have a fairly similar train and test scores. What differenciates the models are their training times. Even though test score for KNN is slightly lower that Logistic Regression and SVC, the training time is much lower for KNN.
For this specifc reason we decided to look further with KNN rather than the other models

When we look at the preliminary confusion matrix for the training dataset we see that we have quite a few false negatives and false positives.

![App Screenshot](/images/confusionTraining.png)

Can this be improved upon by trying to balance the dataset?
We did this by using the RandomOverSampler to oversample the positive class records got a dataset of 2657 positive records and 2560 negative records.

After trainging the KNN model with the oversampled training dataset, we were able to see that it improved to reduce the number of false positives and false negatives.

![App Screenshot](/images/oversampledConfusion.png)

We then predicted the classes for the larger unseen dataset to see what our confusion matrix looked like but it seems that the false postives rose by quite a bit.

![App Screenshot](/images/unseenConfusion.png)

So in our case, maybe oversampling isn't the best approach.

### Recommendation

I would select the KNN Classifier because has a lower training time but similar train/test score other classifiers.
