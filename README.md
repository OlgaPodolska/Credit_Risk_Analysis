# Credit_Risk_Analysis
Using Supervized Machine Learning algorithms as Resampling, SMOTEENN, BalancedRandomForestClassifier and  EasyEnsembleClassifier to predict credit risk for unbalanced credit cards dataset.

## Overview of the analysis

Dataset from LendingClub: LoanStats_2019Q1

<a href="https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Grocery_v1_00.tsv.gz">here at S3 service on AWS</a>  

**Used tools:**
numpy                     1.21.5  
pandas                    1.16.0
scipy                     1.7.3  
scikit-learn              2.2.0
imbalanced-learn          0.9.0
RandomOverSampler
SMOTE algorithms
ClusterCentroids algorithm
SMOTEENN algorithm
BalancedRandomForestClassifier (bias reduction model)
EasyEnsembleClassifier (bias reduction model)

## Results

### 1. Using Resampling Models to Predict Credit Risk 
Using my knowledge of the imbalanced-learn and scikit-learn libraries, I evaluated three machine learning models by using resampling to determine which is better at predicting credit risk. First, I used the oversampling RandomOverSampler and SMOTE algorithms, and then I used the undersampling ClusterCentroids algorithm. Using these algorithms, I resampled the dataset, viewed the count of the target classes, trained a logistic regression classifier, calculated the balanced accuracy score, generated a confusion matrix, and generated a classification report.

### Naive Random Oversampling

![img1.png](/images/img1.png) 

Balanced Accuracy: 0.6497536370265621
Precision: The precision is low for High-risk loans and is high for Low-risk loans.
Recall: High/Low risk = .62/.68

### SMOTE Oversampling

![img2.png](/images/img2.png) 

Balanced Accuracy: 0.6443721269403855
Precision: The precision is low for High-risk loans and is high for Low-risk loans.
Recall: High/Low risk = .63/.66

### Undersampling ClusterCentroids algorythm

![img3.png](/images/img3.png) 

Balanced Accuracy: 0.6443721269403855
Precision: The precision is low for High-risk loans and is high for Low-risk loans.
Recall: High/Low risk = .63/.66


### 2. Using the SMOTEENN algorithm to Predict Credit Risk

Using my knowledge of the imbalanced-learn and scikit-learn libraries, I used a combinatorial approach of over- and undersampling with the SMOTEENN algorithm to determine if the results from the combinatorial approach are better at predicting credit risk than the resampling algorithms. Using the SMOTEENN algorithm, I resampled the dataset, viewed the count of the target classes, trained a logistic regression classifier, calculated the balanced accuracy score, generated a confusion matrix, and generated a classification report.

### Combination (Over and Under) Sampling

![img4.png](/images/img4.png) 

Balanced Accuracy: 0.6443721269403855
Precision: The precision is low for High-risk loans and is high for Low-risk loans.
Recall: High/Low risk = .70/.57

### 3. Using Ensemble Classifiers to Predict Credit Risk  

Using your knowledge of the imblearn.ensemble library, you’ll train and compare two different ensemble classifiers, BalancedRandomForestClassifier and EasyEnsembleClassifier, to predict credit risk and evaluate each model. Using both algorithms, you’ll resample the dataset, view the count of the target classes, train the ensemble classifier, calculate the balanced accuracy score, generate a confusion matrix, and generate a classification report.

### Balanced Random Forest Classifier

![img5.png](/images/img5.png) 

Balanced Accuracy: 0.7885466545953005
Precision: The precision is low for High-risk loans and is high for Low-risk loans.
Recall: High/Low risk = .70/.86


### Easy Ensemble AdaBoost Classifier

![img6.png](/images/img6.png) 

Balanced Accuracy: 0.9316600714093861
Precision: The precision is low for High-risk loans and is high for Low-risk loans.
Recall: High/Low risk = .92/.94



## Summary

In reviewing all six models, the <mark>EasyEnsembleClassifer model</mark> yielded the best results with an accuracy rate of 93.2% and a 9% precision rate when predicting "High Risk candidates. The sensitivity rate (aka recall) was also the highest at 92% compared to the other models. The result for predicting "Low Risk" was also the highest with the sensitivity rate at 94% and an F1 score of 97%. Therefore, if a model needed to be recommended to perform this type of analysis, then this one would be the clear choice.

Ranking of models in descending order based on "High Risk" results:

- [x] <mark>EasyEnsembleClassifer</mark>: 93.2% accuracy, 9% precision, 92% recall, and 16% F1 Score
- [ ] <mark>BalancedRandomForestClassifer</mark>: 78.9% accuracy, 3% precision, 70% recall and 6% F1 Score
- [ ] <mark>SMOTE</mark>: 65.2% accuracy, 1% precision, 61% recall and 2% F1 Score
- [ ] <mark>SMOTEENN</mark>: 64.5% accuracy, 1% precision, 72% recall and 2% F1 Score
- [ ] <mark>RandomOverSampler</mark>: 64.0% accuracy, 1% precision, 66% recall and 2% F1 Score
- [ ] <mark>ClusterCentroids</mark>: 54.5% accuracy, 1% precision, 69% recall and 1% F1 Score

A side note that should be considered is that original dataset had 99% of the applications classified as "Low Risk" with only 1% of the data classified in the "High Risk" category. This may skew the results greatly as there is a risk that the Machine Learning algorithms are creating clusters drawing from too small of a dataset of actual "High Risk" applications. This margin of risk might not be something that banks would be comfortable accepting.