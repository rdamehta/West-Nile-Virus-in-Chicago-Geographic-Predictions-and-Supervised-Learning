# West Nile Virus in Chicago, Geographic Predictions, and Supervised Learning


## Table of Contents
- [Introduction](https://github.com/rdamehta/west-nile-project_ravi/blob/master/README.md#introduction)
- [Exploratory Data Analysis](https://github.com/rdamehta/west-nile-project_ravi/blob/master/README.md#eda)
- [Heatmaps](https://github.com/rdamehta/west-nile-project_ravi/blob/master/README.md#heatmaps)
- [Model Results](https://github.com/rdamehta/west-nile-project_ravi/blob/master/README.md#modeling--results)
- [Powerpoint Presentation Link](https://github.com/rdamehta/west-nile-project_ravi/blob/master/Using%20Machine%20Learning%20to%20Predict%20West%20Nile%20Spread.pptx)
### Introduction
This project was particularly fascinating to me for a multitude of reasons. 
 
Having actually suffered and recovered from malaria, I was interested in how mosquito vectors could spread other diseases, and with my background in public health and medicine I wanted to know how West Nile spread in Chicago. 

I got the inspiration from browsing kaggle datasets as we data scientists do looking for interesting things to play around with. This is the **[kaggle competition](https://www.kaggle.com/c/predict-west-nile-virus/)** for those interested.

### EDA
The task at hand was to predict where West Nile Virus would show up based on data collected from the various mosquito traps dispersed through the greater Chicago region. There were 8 species of mosquitos collected, but a vast majority of them were some type of Culex Pipiens/Restuans. Here is the distribution of positive West Nile cases by Species for every time data was collected from a mosquito trap.

<img src="https://github.com/rdamehta/rdamehta.github.io/blob/master/img/Species.png" alt="species" style="width: 700px;"/>

Additionally I had weather data available to me over the dame time period West Nile was running rampant through Chicago. This was vitally important since mosquito breeding season are the summer months, and mosquitoes prefer humid, tropical climates, and they don't like rain. Here is the weather data, with min and max temperature, wetbulb, and dewpoint for humidity analogs. 

<img src="https://github.com/rdamehta/rdamehta.github.io/blob/master/img/weather.PNG" alt="weather" style="width: 710px;"/>

Now onto the Heatmaps

### First things first: Heatmaps year by year for the training data
Training data was data from the odd years between 2007 to 2013. The testing data set contained the even years and I treated it as sacred

2007

<img src="https://github.com/rdamehta/rdamehta.github.io/blob/master/img/2007.PNG" alt="2007" style="width: 400px;"/>

2009

<img src="https://github.com/rdamehta/rdamehta.github.io/blob/master/img/2009.PNG" alt="2009" style="width: 400px;"/>

2011

<img src="https://github.com/rdamehta/rdamehta.github.io/blob/master/img/2011.PNG" alt="2011" style="width: 400px;"/>

2013

<img src="https://github.com/rdamehta/rdamehta.github.io/blob/master/img/2013.PNG" alt="2013" style="width: 400px;"/>


And here is where they placed the traps:

<img src="https://github.com/rdamehta/rdamehta.github.io/blob/master/img/traps.png" alt="traps" style="width: 400px;"/>

### Modeling & Results


So on to the modeling! After cleaning, feature engineering, and merging the weather data and training data collected from the traps I decided to make a random forest classifier. However we had one issue: we had some seriously unbiased classes.
- West Nile negative: 9955 cases
- West Nile positive: 551 cases.

To combat this and prevent my model from just predicting zeros and calling it a day, I oversampled the minority classes. Essentially I artificially created more positive cases to match a 1:1 ratio with the negative cases using a technique call MICE. But first I split my data, and oversampled one split, and used the other split as a holdout set to test my model against. 

Here are my results for the Random Forest Classifier:

<img src="https://github.com/rdamehta/rdamehta.github.io/blob/master/img/RFROC.PNG" alt="Random Forest" style="width: 400px;"/>

Also tried out a Neural Network with these results:

<img src="https://github.com/rdamehta/rdamehta.github.io/blob/master/img/NNROC.PNG" alt="Neural Network" style="width: 725px;"/>

As you can see a relatively simple Neural Network outperformed the Random Forest Classifier. It would be interesting to see how a boosting algorithm would perform!

