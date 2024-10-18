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

### Recommendation

I would select the KNN Classifier because has a lower training time but similar train/test score other classifiers.
