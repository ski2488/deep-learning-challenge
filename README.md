# deep-learning-challenge
UT Module 21

# Overview
  The purpose of this module was to apply deep learning to predict the success or failure of investments made by the nonprofit foundation Alphabet Soup. The data set included ~34,000 investments and had details for each investment such as: income, amount asked for, organization type, etc. 

# Data Preprocessing
  - The target variable for this exercise was the 'IS_SUCCESSFUL' field, which is a binary classification.
  - The various independent variables included the integer 'Ask Amount' as well as categoricals such as: application type, affiliation, classification, etc. Many of these categorical variables included a high number of dimensions, so cutoffs were selected to aggregate less frequent categories into an 'Other' label. Then, each of the  categorical variables was made into a dummy variable
  - The 'EIN' and 'NAME' variables were eliminated as they don't provide predictive power

# Compiling, Training, and Evaluating the Model
  For this exercise I ran 4 models in order to try to incrementally increase the predictive power:
  - Original Model -  
                   - general data cleansing, reducing the dimensionality of 'APPLICATION_TYPE' and 'CLASSIFICATION', converting categoricals to dummy variables.
                   - 2 hidden layers (80 nuerons, 30 nuerons, activation function: 'relu')
                   - 100 epochs
                   - test data accuracy rate of 0.7335
  - Optimize Model #1 (Additional Data Preprocessing) - 
                   - further dimension reduction, now applied to variables: 'AFFILIATION', 'USE_CASE', 'ORGANIZATION', 'INCOME_AMT'
                   - 2 hidden layers (80 nuerons, 30 nuerons, activation function: 'relu')
                   - 100 epochs
                   - test data accuracy rate of 0.7269
  - Optimize Model #2 (log(ASK_AMT))- 
                   - create variable for log2(ASK_AMT) due to the massive spread of values for this variable
                   - 2 hidden layers (80 nuerons, 30 nuerons, activation function: 'relu')
                   - 100 epochs
                   - test data accuracy rate of 0.7336
  - Optimize Model #3 (Auto Optimize)- 
                   - use keras_tuner library to search for best combination of activation function (tanh vs relu), # layers (2 -4), # nuerons (50 - 100) 
                   - Selected Model: activation: tanh, 3 layers (100 nuerons, 100 nuerons, 70 nuerons)
                   - 25 epochs
                   - test data accuracy rate of 0.7371

# Summary: 
The optimized model is #3 in which I used the keras_tuner to search for the hyperparameters which maximized the prediction accuracy. This model used a tanh activation function with three hidden layers. Unfortunately, I did not get to a 75% accuracy but did outperform the other three models which were comprised of static assumptions. 
