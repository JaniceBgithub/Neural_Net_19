# Neural_Net_19

## Base Case
- Drop EIN and Name
- Binned application type into 6 bins 
- Binned classification into 7 bins 
- Ran with two hidden node layers.  First hidden node layer has 24 neurons, second hidden node layer has 12 neurons
- First and second layer activation was relu, output layer activation was sigmoid
- Model optimizer was adam and loss was binary crossentropy
- 100 epochs

- Accuracy was 0.7224, loss 0.5574

## Remove the second hidden layer

Same as base case, but remove the second hidden layer.

Accuracy was 0.7259, loss was 0.5582.  Performance improved slightly with a simpler model 

## Remove second layer, 12 neurons in first layer, activation = swish

Accuracy was 0.7242.  Slight decline in performance vs the relu activation. 

## Remove second layer and neurons in first layer down to 12

Accuracy was 0.7258 in baes case.

Dropped the income amount and status with basically no change in the model - 0.7251 accuracy. Used a random forest and shap plot to determine feature importance. 

![shap plot](https://github.com/JaniceBgithub/Neural_Net_19/blob/main/Resources/19.1-shap.png)


## Epochs

In the above results, ran with 100 epochs.  Try 1000 with above (dropped income amount and status, 1 layer downt o 12 nuerons and relu)


