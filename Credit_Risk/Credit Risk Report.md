# Credit Risk Analysis Report

## Overview of the Analysis

**Purpose:**
The pupose of analysing the historical lending data is to build a model that can identify the creditworthiness of borrowers so as to understand the risk involved with different borrowers based on their income, existing debts, etc which inturn helps the banks in decision making process.

**Data**
- The data used for this analysis has the information like loan amount, interest rate, borrower income, The ratio of borrower's total debt to income, borrower's number of accounts, credit score, total debt and the loan status.
- The entire data has 77536 records and by performing the value_counts operation to the loan status column, it is observed that 75036 has `0` indicating the`Healthy loans` where as 2500 are `1` meaning they are the `High-Risk loans`

**Machine Learning Process:**

**Step-1: Read the data and get the labels and features**

- Read the data from the csv file in Resources folder into a Pandas DataFrame and review the dataframe to know the type of information available in the csv file

- Separate the data into labels(y) and features(X). As the target variable is `loan_status`, I have separted that column from the table to get the y label and dropped `loan_status` from the rest of the table to get the features i.e., X


**Step-2:Split the Data into Training and Testing Sets** 

- To split the data into training and testing sets, I have imported the `sklearn.model_selection`and used the `train_test_split`function.

**Step-3: Creating Logistic Regression Model**

- Using Logistic Regression Modwl as the label is a binary classification and it uses the concept of the threshold value, which defines the probability of either 0 or 1. 

- To create this model, imported `LogisticRegression` from `sklearn.linear_model`and created an instance followed by fitting the model using training data.

- Made the predictions on the testing data labels by using the testing feature data (`X_test`) and the fitted model.

**Step-4: Evaluate the model's performance**

- To evaluate the model, created the confusion matrix and Classification Report functions from sklearn.metrics library.


## Results

- The results of confusion matrix: 

[[18663   102]

[   56   563]]

- True Positives: 18663 represents the number of instances where the model correctly predicted that borrowers are creditworthy (positive class) and they are actually creditworthy.
- False Positives: 102 represents the number of instances where the model incorrectly predicted that borrowers are creditworthy (positive class) when they are not actually creditworthy.
- False Negatives: 56 represents the number of instances where the model incorrectly predicted that borrowers are not creditworthy (negative class) when they are actually creditworthy.
- True Negatives: 563 represents the number of instances where the model correctly predicted that borrowers are not creditworthy (negative class) and they are actually not creditworthy.

- The results of classification report:

              precision    recall  f1-score   

           0       1.00      0.99      1.00    
           1       0.85      0.91      0.88       

- Accuracy : 0.99

## Summary

Looking at the classification report, we see that:
- For class 0 (healthy loans), the model achieves high precision, recall, and F1-score, all close to 1. This indicates that the model performs very well in correctly identifying healthy loans.
- For class 1 (loans at high risk of defaulting), the precision, recall, and F1-score are lower compared to class 0, but still reasonable. The precision of 0.85 means that when the model predicts a loan as high risk, it is correct approximately 85% of the time. The recall of 0.91 indicates that the model captures approximately 91% of all actual high-risk loans.
However, given the context of loan status, where correctly identifying loans at high risk is crucial for risk management, the metrics for class 1 are more important in this context. 

- Therefore, while the model performs exceptionally well for healthy loans (class 0), it performs relatively well but with room for improvement for loans at high risk of defaulting (class 1).
