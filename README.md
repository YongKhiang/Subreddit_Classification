# Project 3: Subreddit Classification

## Problem Statement

Recently,there is an inflow of irrelevant posts on Apple and Android subreddits and Reddit has received many complaints from the end users. In an attempt to salvage their reputation, Reddit is looking to find a permanent fix to solve the issue by leveraging machine learning to distinguish between Apple and Android subreddit posts. Consequently, the load on the content moderators could be eased and millions of users could also benefit in finding relevant posts of their interest on the subreddits. 

The goal of this project is to develop a machine learning binary classifier and gain insights on the features which could accurately separate posts into Apple or Android subreddits, using natural language processing techniques. The performance of the different classifier models would be evaluated using the Receiver Operating Characteristic-Area Under Curve (ROC-AUC) metric which tells how good the classifier is in distinguishing between Apple and Android subreddits, with a success criteria of above 0.95 (ideal being 1.0) while preserving model generalizability.

## Executive Summary

The data was collected by scrapping posts from the two popular subreddits and then training the model on 80% of the data and using the other 20% as the unseen test set to evaluate the production model performance. 

In the exploratory data analysis, it was found that there are differences in the common words and phrases which could help distinguish the two subreddits. For r/Android, topics related to different phone models e.g. Samsung Galaxy, Note and Pixel phones are frequently posted while for r/Apple, tech support and apple watch topics are heavily posted.  

Four classification models using natural language processing techniques were evaluated in their predictive performance to correctly classify r/Apple and r/Android subreddit posts. The Logistic Regression model with text & title feature as predictor slightly outperformed the other models with a high cross-validation ROC-AUC score of 0.986.

The model's performance against unseen test data was maintained at a high ROC-AUC score of 0.981 indicating good model generalizability, with corresponding overall accuracy of 94.8% and a very low misclassification rate of r/Apple and r/Android subreddit posts at 3.3% and 7.7% respectively. It was found that most of the misclassifications are a result of common words appearing between the 2 subreddits e.g. discussion between android and apple product features in r/apple and vice versa, or short text without strong word features.

To further improve the logistic regression classifier's performance, additional features could be explored e.g. a bigger corpus that incorporates more vocabulary on technology by extracting the text of the posts' comments to address the model's shortcomings at classifying posts with short text, or conducting sentiment analysis on the text features as some of the posts could be personal rants against some products.

Additionally, the data could be trained on different classifier models e.g. Subject Vector Classifier or Random Forests to compare their classification performance.

Lastly, in order to maintain the classifier's performance, new data should be continued to be pulled periodically to add to the dataset, so as to account for changing trends in technology topics in r/Apple and r/Android.

### Contents:
- [Data Collection](./code/01_Webscrapping_and_Data_Collection.ipynb#Data-Collection)
- [Data Cleaning](./code/02_Data_Cleaning_and_EDA.ipynb#Data-Cleaning)
- [Exploratory Data Analysis](./code/02_Data_Cleaning_and_EDA.ipynb#Exploratory-Data-Analysis)
- [Pre-processing](./code/03_Preprocessing_Modelling_and_Insights.ipynb#Pre-processing)
- [Modelling](./code/03_Preprocessing_Modelling_and_Insights.ipynb#Modelling)
- [Production Model](./code/03_Preprocessing_Modelling_and_Insights.ipynb#Production-Model)
- [Conclusion and Recommendations](./code/03_Preprocessing_Modelling_and_Insights.ipynb#Conclusion-and-Recommendations)

## Data Dictionary

|Feature|Type|Dataset|Description|
|---|---|---|---|
|subreddit|str|android/ apple subreddits|The name of the subreddit|
|selftext|str|android/ apple subreddits|The body text of each subreddit post| 
|title|str|android/ apple subreddits|The title of each subreddit post|
|upvote_ratio|float|android/ apple subreddits|The number of upvotes a post has, divided by the total number of votes the post received|
|score|float|android/ apple subreddits|The number of upvotes a post has|
|num_comments|float|android/ apple subreddits|The number of upvotes a post has| 
