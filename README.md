# Costa Rica Poverty Prediction Kaggle Challenge


## Executive Summary
There are a huge number of social programs, having a hard time finding the right set of people to address. It becomes tricky when it comes to the segmentation of poverty levels and focusing on the poorest segment available. The goal is devising a model for more appropriate means of classifying household into different levels of poverty for Costa Rica. It is challenging to decide on factors contributing to the poverty line, many such programs are currently going on, and still, the problem of determining the right threshold for poverty line remains unsolved. The objective is to predict poverty on a household level. Moreover, we must predict for every individual, but we should relate them to each household to predict poverty on a household basis. An exploratory data analysis was done with the data set. Categorial and non-categorical data columns were studied in detail. Redundant columns were removed, and highly correlated variables were also removed from data set. The data was prepared for mining and desired solutions were developed. The performance of these solutions was evaluated, and best model was selected. The best method of classification was undoubtedly the random forest because of its highly auc. The number of trees used for training and averaging were 300 which served a good purpose for giving an AUC score of 0.97. A data mining solution was developed and formulated to classify the household into different levels of poverty

## Background and Introduction

Problem Statement 
It is challenging to decide on factors contributing to the poverty line, many such programs are currently going on, and still, the problem of determining the right threshold for poverty line remains unsolved. It is not often easy to segregate poverty levels for different households and it is challenging to keep these results biased for equality. The problem here is to find an optimum solution over the traditional econometrics which might improve the overall process. Using the data given by IDB (Inter-American Development Board) for Costa Rica, we need to address the problem by categorizing households into four categories – extreme, moderate, vulnerable, and non-vulnerable. Apart from Costa Rica, the problem accounts for generalizing a machine learning algorithm that needs to address the poverty issues for other countries as well Provide a brief introduction to the opportunity and significance (why you study the particular use case). 

## Goal of Study
Recently, many initiatives are being taken for the eradication of poverty. There are a huge
number of social programs, having a hard time finding the right set of people to address. It becomes tricky when it comes to the segmentation of poverty levels and focusing on the poorest segment available. The poorest typically can’t prove whether they qualify, as they can’t provide the necessary income and expense records. At present, one of the most viable methods to verify the income level qualification is the Proxy Means Test (PMT). Through PMT, many agencies include a family’s noticeable household attributes like the material of their walls and ceiling or the assets found in the home for their models to classify them and predict their level of need. The goal is devising a model for more appropriate means of classifying household into different levels of poverty.

## Possible Solution
The objective is to predict poverty on a household level. Moreover, we must predict for every individual, but we should relate them to each household to predict poverty on a household basis. As we are segmenting on the level of poverty, this will be a supervised multi-class classification machine learning problem:
Supervised: provided with the labels for the training data
Multi-class classification: Labels are discrete values with 4 classes.
First, we get introduced to the problem, then perform a thorough Exploratory Data Analysis of the dataset, work on feature engineering, try out multiple machine learning models, select a model, work to optimize the model, and evaluate its performance. Finally, inspect the outputs of the model and draw conclusions.




## Data Exploration and Visualization
As a part of data exploration and visualization, the process was lengthy and complicated. We had to overcome the challenge of analyzing 142 columns to such a level that significance of them had to be kept in mind. Few of the columns had null values which had to be given importance as well. Instead of simply ignoring such values, an optimum solution was to be given a thought. As a result the data exploration and visualization was done in the following manner.

Null Analysis: After running analysis following columns contained null values 

 

Detailed exploration was required to ensure what can be done to get rid of such values. We observed each of the attribute and presented the findings according. 

Distribution of meaneduc and SQBmeaned : The two attributes had 5 missing values.
As we can observe that this particular attribute has several outliers. An optimum value should be chosen to fill these missing values, considering mean would be a bad idea. For the same reason, we chose to replace these 5 values with median of the column Meaneduc.
Same goes for the SQBMeaned column, 5 missing values were replaced by median of SQBMeaned.

V21a1 : 

 

The column can be ignored since it contains 72% missing values. Replacing the values can overfit the model so the best idea is to get rid of the column.

V18q1 :

 

Again this column can be ignored since it contains 77% missing values. Replacing the values can overfit the model so the best idea is to get rid of the column.

Rez_esc :
This column also has 83% missing values, got rid of this column too.
 

Exploring Binary Columns : There were 102 Binary columns (categorical) in the dataset. All the columns were one hot encoded based. There was challenge of analyzing the distribution of the columns containing 1s and 0s. User defined functions were formulated to visualize the histogram of these columns. The task of reducing and optimizing the model would have achieved by removing columns containing 97% or more 1s or 0s. Such columns were removed from the data set. Some of the columns had distribution like :

Hacapo :

 
This particular column as seen as 97% 0s in it. This particular column can be eradicted from the dataset.

V14a :

This column  as shown on next page has 99.48% of 1s and hence is removed from the data set.




 

Planpri :

  

Exploring Numerical Columns : The analysis of 35 numerical columns was to be performed to get valuable insights. This was carried out by visualizing the dependence of every column on other. For this, correlation came into picture which stated how these 35 numerical columns interacted with each other. Heat map was used to visualize the correlations among these numerical columns.


 
## Correlation of Numerical Columns 

As a part of data preparation, we needed to analyze the correlations. Set of highly correlated both positively and negatively was needed to study further details. Highly correlated variable should be removed as a part of data cleaning process. These variables are redundant while applying them to algorithm.


III. Data Preparation and Preprocessing
As a part of data preparation, we explored different aspects of the dataset. Starting from breaking down of data to segregating them in form of binary and numerical, the dataset was broken into such level of details. 

When we observed that few of the binary columns contained more than 97% of 1s or 0s we got rid of such attributes. This was the very first step of data preparation for our project. We created user defined functions to optimize our work and instead of visualizing and analyzing plot of 80 different columns we wrote mathematical equations and subsequently removed the columns. 








Before data preprocessing :

 
Correlation of Numerical Columns 

While preparing the numerical data for analysis, we studied the correlations and removed the variables which had high level of correlation with other variables. This was a major step to prepare numerical data and process it. The earlier heatmap of correlations showed that there were many numerical columns having strong correlations. We removed them and the optimized heatmap with fewer variables was obtained. The following figures illustrate the same.

After processing and removing highly correlated variables :
 
In this way, the data was processed and we reduced the columns from 142 to 85 which led to massive reduction in the data set and the dataset was ready for applying mining solutions.
IV. Data Mining Techniques and Implementation
The problem suggested was of classification, more precisely multi class classification. We explored various data mining techniques as appropriate to our solution. The following algorithms were applied for the dataset :

1.	KNN (K-Nearest Neighbor Algorithm) :
KNN was applied to our dataset to classify the household based on 85 attributes. While applying KNN, we needed to split the data set into training and testing data set in order to validate its accuracy. It was equally challenging to find a good value of K which gave a maximum accuracy for KNN. Using the testing data set we predicted values for the poverty levels of different testing household data.

 

After performing dry run, we got maximum accuracy for k=78

Confusion Matrix 

 

2.	Naïve Bayes Classifier : We trained our datset on Naïve Bayes classifier as well. We wanted to verify whether all of the attributes are dependent on each other or not. Even though this was a try, lot of interpretations were made from this considering the dependency of household properties on each other. We assumed that these attributes were strongly dependent on each other however they weren’t from the accuracy that we got from this classifier.

 

	Confusion Matrix 

	 

3.	Decision Tree : While classifying a particular household, we normally in real life might use decision tree itself. So studying property of this model was equally important for us. Training a decision tree for classification model was done and results were obtained.

 

	Confusion Matrix

	 

4.	Linear Discriminant Analysis : Solving a classification problem while reducing the dimensions of 89 would surely be a good idea to approach the scenario. We performed LDA on our dataset to check if the results were good by reducing the dimension.

 

 

5.	Support Vector Machines : Implementation of support vector machines with different kernals was done. Using SVMs ensured that the data was separated linearly by projecting them to different levels of axes.

 

 
 
	 

6.	Random Forest Classification : As we observed, during decision tree few classes were not predicted. It is advisable to use many trees i.e ensemble of trees to proceed for the solution. Random forest, trees were varied from 200 to 500 with gaps fo 50 and best results were obtained for trees =300.

 

Confusion Matrix 
 

## Performance Evaluation
As a result of asymmetrical distributions of classes a more strong performance evaluator was needed to ensure the solution isn’t biased. We didn’t make use of accuracy calculated from the confusion table. The reason being that the sample had more predictions of class 4 and we didn’t want to move towards best accuracy with a false behavior. For the same, we evaluated the models based on multi class auc score. It was not possible to visualize the ROC curve because we had 4 outcome variables. 

Every model, we checked the AUC score and the results were obtained in the following manner :

1.	KNN : for the best possible k = 78 : AUC = 0.64

 

2.	Naïve Bayes : The model increased the AUC score to 0.70 from KNN model 

 

3.	Decision Tree : The decision tree had AUC score of 0.59

 

4.	Linear Discriminant Analysis : AUC Score : 0.72

 

5.	Support Vector Machine : AUC Score : 0.78

 

6.	Random Forest : AUC Score : 0.97

 

The best method of classification was undoubtely the random forest because of its highly auc. The number of trees used for training and averaging were 300 which served a good purpose for giving an AUC score of 0.97.

## Discussion and Recommendation
The overall approach was to classify the hold of Costa Rica based on the information which we received from the board. The aim was to do this in an unbiased manner. There would have been a strict policy rules which to determine the poverty status as it constitutes a major part in country’s growth. 

The advantages were lot of information was provided for the classification problem. Around 142 attributes of particulate household were sufficient for us to come to conclusion. The disadvantage was that the limited sample size could some way affect the generalized model and might prove wrong at times. The recommendation would be getting more data in terms of households for a more accurate model.

## Summary

The objective to categorize the households of Costa Rica into four levels of poverty was achieved by designing the model. When the data had different attributes from families our aim is to reduce the redundant variables and get a optimum dataset of the development of machine learning model. An exploratory data analysis made us to work on feature engineering of various attributes of household and then making data ready for data mining solution. After designing models, it was important for us to evaluate the performance of model so that it doesn’t perform in unbiased manner. Therefore, a data mining solution was developed and formulated to classify the household into different levels of poverty.

