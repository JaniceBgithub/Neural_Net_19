# Neural_Net_19

## Overview of the Analysis
This analysis uses 34,000 organizations that have received funding from Alphabet Soup over the years. 

The goal of this analysis is to predict whether the money was used successfully with a binary classifying neural network model.  

## Targets and Features

Within this dataset are a number of columns that capture metadata about each organization, such as the following:

Target: 
- IS_SUCCESSFUL—Was the money used effectively

Features: 
- APPLICATION_TYPE—Alphabet Soup application type
- AFFILIATION—Affiliated sector of industry
- CLASSIFICATION—Government organization classification
- USE_CASE—Use case for funding
- ORGANIZATION—Organization type
- STATUS—Active status
- INCOME_AMT—Income classification
- SPECIAL_CONSIDERATIONS—Special consideration for application
- ASK_AMT—Funding amount requested


Not used in the model:
- EIN and NAME—Identification columns

## Compiling, Training and Evaluating the Model 

### Base Case

The base case included the following steps: 

- Drop EIN and Name
- Binned application type into 6 bins 
- Binned classification into 7 bins 
- Ran with two hidden node layers.  First hidden node layer has 24 neurons, second hidden node layer has 12 neurons
- First and second layer activation was relu, output layer activation was sigmoid
- Model optimizer was adam and loss was binary crossentropy
- 100 epochs

- Accuracy was 0.7224, loss 0.5574

These layers, neurons and bins were used because increasing them did not seem to add to model accuracy. 

The following sections are the optimization steps that were taken to improve model accuracy: 

### Remove the second hidden layer

Same as base case, but remove the second hidden layer.

Accuracy was 0.7259, loss was 0.5582.  Performance improved slightly with a simpler model 

### Remove second layer, 12 neurons in first layer, activation = swish

Accuracy was 0.7242.  Slight decline in performance vs the relu activation. 

### Remove second layer and neurons in first layer down to 12

Accuracy was 0.7258 in base case.

Looked at a heatmap for insight into features to drop:

![heat](https://github.com/JaniceBgithub/Neural_Net_19/blob/main/Resources/19-3-HEAT.png)

Dropped the income amount and status with basically no change in the model - 0.7251 accuracy. (Used a random forest and shap plot to determine feature importance).

Then looked at impact of further simplifying the model and used 8 neurons in the first layer.  Result was only a very small drop in accuracy of 0.7241.

![shap plot](https://github.com/JaniceBgithub/Neural_Net_19/blob/main/Resources/19.1-shap.png)

### Best performance

- 100 epochs
- 2 hidden layers (12 nodes in layer 1, 8 nodes in layer 2)
- 1st hidden layer activation - relu
- 2nd layer activation - swish
- dropped income amount and status

- Result was best so far 0.7279

- (500 epochs with above was same result 0.7279)

### Also dropped use case in addition to income and status (others as per best performance section)

 Result was 0.7215, add use case back in!

### Epochs

In the above results, ran with 100 epochs.  Try 1000 with above (dropped income amount and status, 1 layer downt o 12 nuerons and relu).  As shown in the plot, the accuracy was improving with subsequent epochs, although this did not result in higher accuracy when run with the testing data set - likely due to overfitting when running that many epochs.

Accuracy only improved to 0.7283.

![epochs](https://github.com/JaniceBgithub/Neural_Net_19/blob/main/Resources/19.2-epochs.png)

### Changing binning for classification & application type

- Base case was application type = 6 bins and classification = 7 bins
- Changed to 9 & 12
- 1st hidden layer = 12 neurons & relu
- 2nd hidden layer = 8 neurons & swish
- 100 epochs
- Dropped income amount and status
- Accuracy was 0.7248

As per above, but changed bins to 5 & 4, accuracy dropped.

## Summary

The best accuracy achieved with the model was 72.79%. In this case, a simpler model seemed to achieve the best results, most likely due to avoidance of overfitting.

Other models could be used  - a random forest model was also used with similar accuracy results.  This was mainly done so that a Shap plot could be generated to determine feature importance and understand which features could be dropped.  











