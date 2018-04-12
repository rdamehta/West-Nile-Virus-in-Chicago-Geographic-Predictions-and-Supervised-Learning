## West Nile Virus in Chicago, Geographic Predictions, and Supervised Learning
With a background in public health and medicine this project was particularly fascinating to me. Having actually suffered and recovered from malaria, I was interested in how mosquito vectors could spread other diseases, and how west nile got all the way over to Chicago

For the data we decided to attempt to predict West Nile Spread in Chicago based from Kaggle's West Nile competition (linked below). 

- Mapped the mosquito trap locations and places were west nile was found
- Incorporated weather data including temp, wetbulb, sunrise and sunset, and many other conditions and merged them on Date with the Kaggle Training Data
- Created a Random Forest model based on number of features

What was particularly interesting, and something of note, was how imbalanced the classes were in the training data. I had to makes sure to oversample the minority class, but also make sure I had some holdout training data where I did not use SMOTE to oversample the minority class so my model's learning would not leak into all my training data and overfit.

This repository was forked from the Kaggle West Nile Virus competition [Kaggle West Nile (https://www.kaggle.com/c/predict-west-nile-virus/) 

[This file](https://www.kaggle.com/c/predict-west-nile-virus/download/west_nile.zip) sets up the directory structure:

- `input`: this contains all of the data files for the competition
- `working`: on Kaggle, scripts run with this as the working directory. We recommend you do the same thing locally to avoid mixing output files with source files.
- `src`: Source scripts. We've provided some examples to get you started.

