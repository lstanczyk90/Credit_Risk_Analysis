# Credit Risk Analysis

## Project Overview

The purpose of this analysis is to leverage machine learning algorithms using the imbalance-learn and scikit-learn libraries to build and evaluate models to predict credit card risk. Specifically, utilizing data from LendingClub (a peer-to-peer lending services company), the goal of the project is to evaluate a varierty of factors and use them to predict credit risk (defined as high-risk or low-risk). This project focuses on using RandomOverSampler, SMOTE, ClusterCentroids and SMOTEENN over-and-undersamping algorithms to evaluate and compare the outcome of a logistic regression algorithm. We also utilize ensemble classifiers to predict credit risk (namely BalancedRandomForestClassifier and EasyEnsembleClassifier) to evaluate and compare the results.

## Results

### **RandomOverSampler Algorithm**: 

![alt text](https://github.com/lstanczyk90/Credit_Risk_Analysis/blob/a729a2e6bcc0f2e13df478db4b8f41349bc6446c/Screenshots/oversample_reults.png)

- As you can tell from the above screenshot, the balance accuracy score was calculated as 0.66632. This effectively means that 60% of the time our model is effective at predicting credit risk (defined as correct outcomes over total outcomes). Caution, however, should be applied, as we are dealing with an imbalanced dataset that contains much more low_risk factors. 

- Precision is measure of the reliability of positive classifications. Our model yielded a very high precision for low_risk (1.00), but a very poor high_risk precision score. This low precision may mean numerous false positives for our model with regards to high_risk classifications. 

- Sensitivity can be defined as as the ability of our classifiers to locate positive values. Here, we note a sensitivity of 0.70 for high_risk values, and a sensitivity of 0.63 for low_risk values. From the perspective of a credit card company, this may be a more desirable outcome, as our model reflects that we are not seeing many false negatives. False negatives would be dangerous for the credit card company, as it would mean (assuming "high_risk" as a positive outcome) true high risk accounts would be flagged as low risk. In our dataset, sensitivity is more desirable than precision, as we want to be more conservative with how we flag accounts as high or low risk. 

### **SMOTE Algorithm**:

![alt text](https://github.com/lstanczyk90/Credit_Risk_Analysis/blob/a729a2e6bcc0f2e13df478db4b8f41349bc6446c/Screenshots/smote_oversample_results.png)

- Utilizing the SMOTE Algorithm yielded similar results with regards to balanced accuracy, precision and sensitivity as the RandomOverSampler. As such, this model did not yield any tangible improvements.

### **Undersampling Algorithm**:

![alt text](https://github.com/lstanczyk90/Credit_Risk_Analysis/blob/a729a2e6bcc0f2e13df478db4b8f41349bc6446c/Screenshots/undersample_results.png)

- Utilzing undersampling techniques yielded the worst results thus far. 

- Specifically, the balance accuracy score was calculated at 0.54392, which is appreciably lower than the oversampling results. This implies that undersampling has eliminated valuable data from our analysis for the sake of balancing the overal dataset. As such, we do not recommend relying on this methodology. 

- While precision was similar to the other two models, recall/sensitivity suffered. While high_risk values maintained a relatively high degree of sensitivity, low_risk outcomes suffered, as the resulting sensitivity score was 0.39 (implying that this model is seeing too many false negatives which, as discussed above, is not ideal for our analysis).

### **SMOTEENN Algorithm**:

![alt text](https://github.com/lstanczyk90/Credit_Risk_Analysis/blob/a729a2e6bcc0f2e13df478db4b8f41349bc6446c/Screenshots/smoteen_results.png)

- While SMOTEENN saw an improvement over undersampling, the resulting accuracy score is lower than both oversampling techniques used previously (at 0.62289). Additionally, precision remains generally the same, while sensitivty saw a slight degradation from the oversampling techniques (0.65 for high_risk and 0.59 for low_risk).

### **BalancedRandomForestClassifier**:

![alt text](https://github.com/lstanczyk90/Credit_Risk_Analysis/blob/a729a2e6bcc0f2e13df478db4b8f41349bc6446c/Screenshots/Balanced_Random_Results.png)

- The BalancedRandomForestClassifier randomly under-samples each boostrap sample to balance it. 

- Using this classifier proved superior to the other algorithms, as it resulted in an accuracy score of 0.78854 (meaning that the model was able to predict correct results 79% of the time out of the total).

- Precision remains relatively poor for high_risk outcomes, but as discussed above, we are less concerned with precision in this particular use-case.

- The greatest improvements were in sensitivity scores. High_risk sensitivity increased to 0.70, while low_risk increased to 0.87. Again, this implies that we are seeing less false negatives, which is notable from the perspective of the high_risk recall score. In this use case, the worst outcome would be assessing a true high_risk account as a false low_risk account.

### **EasyEnsembleClassifier Algorithm**:

![alt text](https://github.com/lstanczyk90/Credit_Risk_Analysis/blob/a729a2e6bcc0f2e13df478db4b8f41349bc6446c/Screenshots/Easy_Ensemble_Results.png)

- This classifier yielded superior results to all other models. Specifically, we were able to achieve an accuracy score of 0.93166. 

- Similarly, while precision remained relatively unchanged, this algorithm yielded superior results when it comes to sensitivity. Specifically, we noted a recall score of 0.92 for high_risk and 0.94 for low_risk.

## Summary

Based on our overall analysis, it is obvious that the superior algorithm for this specific use case is the EasyEnsembleClassifier. As discussed in detail above, this use case benefits from a more conservative approach, as failing to identify high-risk accounts as high-risk may be detrimental to the credit card company. As such, this conservative approach means that having false positives for high_risk accounts (i.e., identifying true low_risk as high_risk) is better than the opposite. As such, sensitivity should be prioritized and, of all the models used, **EasyEnsembleClassifier** yielded the best results. 

