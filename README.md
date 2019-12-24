### KDD WeFive_HighFive (Group 1)


Team Members:

1. Akhil Chundarathil

2. Akhila Vemana

3. Akshara Gone

4. Keerthi Reddy Kandi

5. Koushik Koritala

# Project Title: Mining and Modeling NYC Airbnb Data.



### Project Objective: 


The project focuses on analyzing NYC Airbnb to predict the ratings of Airbnb based on their location, price range, guests experience (reviews) and other related features. 

### Data and Source Description:

Dataset Link: https://www.kaggle.com/dgomonov/new-york-city-airbnb-open-data/kernels 

The dataset has the following attributes :

* id
* name
* host_id
* host_name
* neighbourhood_group
* neighbourhood
* latitude
* longitude
* room_type
* price
* minimum_nights
* number_of_reviews
* last_review
* reviews_per_month
* calculated_host_listings_count
* availability_365
* RATINGS ( 1-5 : 1- Lowest, 5- Highest ).This column is not included in dataset, this target variable is added during the data preparation phase.

### CRISP-DM Process:


### 1.Business/Research Understanding Phase : 

**Domain Knowledge**: https://medium.com/airbnb-engineering/contextualizing-airbnb-by-building-knowledge-graph-b7077e268d5a

As Airbnb moves towards becoming an end-to-end travel platform, it is increasingly important for us to deliver travel insights that help people decide when to travel, where to go, and what to do on their trips. 

For example, 

* what are the most popular landmarks and neighborhoods in New York for a reasonable price?  
* Which Airbnb listings are best for families? 
* What are the type of reviews about an Airbnb? 


To scale our ability to answer these travel queries, we needed a systematic approach to storing and serving high-quality information about entities (e.g. ratings, cities, landmarks, events, etc.) and the relationships between them (e.g. the most popular landmark in a city for a reasonable price, the best neighbourhood to stay, etc.)

### 2.EDA and Data Preparation:


* A new "ratings" column is added based on the Airbnb location(neighborhood), price, reviews and days of availability.
(**Domain Knowledge** : https://www.airbnb.com/help/article/1257/how-do-star-ratings-work 

* Imputation techniques performed to handle missing values.
* Based on the statistical information of the dataset the Outliers are removed. 
* Feature Scaling on some of the attributes are performed.
* Dropped some of the features which are not required for further phases.
* Next in Data Exploration, we get useful insights by visualizing different types of graphs plotted (Insights are added as markdown in code).

### 3.Machine Learning:

For modeling, based on the dataset we use:


* Association : We will use apriori algorithm for finding association rules between the attributes in our dataset. apriori class from apriori library will be used to find out the association rules between selected attributes like location,price and rating. min_lift parameter is used as a measure in the generating the association rules.
* Pipelining : We used pipeling for data preparation, feature extraction and modelling. Using normalization or standardization on the entire training dataset before learning would not be a valid test because the training dataset would have been influenced by the scale of the data in the test set. So we used pipelining to prevent this data leakage. We used FeatureUnion in pipeline which allows the results of multiple feature selection and extraction procedures to be combined into a larger dataset on which a model can be trained.
* Ensembling : By combining individual models, the ensemble model tends to be more flexible(less bias) and less data-sensitive (less variance). In our project, We are planning to use Random forest Algorithm as an ensemble model using bagging as the ensemble method and decision tree as the individual model.
 

### 4.Evaluation:

For the performance evaluation, we use the metrics R2 score for Ensembling method, cross_val_score for Pipelining.

### 5. Bias: 
The common definition of data bias is that the available data is not representative of the population or phenomenon of study. Data bias occurs due to structural characteristics of the systems that produce the data. The huge success of applications of machine learning (ML) applications in the past decade — in image recognition, recommendation systems, e-commerce and online advertising — has inspired its adoption in domains such as social justice, employment screening, smart interactive interfaces such as Siri, Alexa, and the like. Along with the proliferation of these applications, there has been an alarming rise in reports of gender, race and other types of bias in these systems. 

There is no bias in our dataset because of the absence of bias causing columns like gender,race etc. So there is no requirement for bias mitigation in our project.


### 6. Summary:

Our dataset is of Airbnb data which is an growing field. Every tourist now-a-days
are likely to prefer Airbnb for their stay rather than hotels. So this is an on going
trend. Our data is unique in terms of helping the users to quickly identify and get
some useful insights about current Airbnb’s located in Newyork.

<p>We cleaned and performed EDA on our dataset before performing modelling.
Some of the original attributes were irrelevant, we performed dimensionality
reduction and handled outliers by removing them, incase of missing values we
used data imputation method of filling with relevant value, we did perform
feature scaling for necessary attributes(reviews), handled some of original
attributes which were of wrong data type by converting it to relevant data type.

<p>There was no imbalance of data in our dataset, so we didn&#39;t perform related
techniques to handle such imbalance. We created a new important feature
“rating” by which customers get to know more about Airbnb. Based on others
features like which neighbourhood the Airbnb is located, their price range, and
their availability in a year.

<p>Association rules, Ensembling technique, Pipelining(PCA , selectkbest,
randomforest) modelling techniques are used to build our model. R2 score is used
for ensembling, cross validation score is used for pipelining to evaluate our
model.
    
<p>During the modelling phase, when we initially tried to do Random forest
modelling we got a score of 0.45, to overcome this problem we performed
“Gridsearchcv” on the random forest regressor model. This enhanced the score to
0.71 which is optimal score and tells that our model is accurate.

<p>Futurework: We have done our project on narrow scope like considered only one
region in US i.e Newyork. This can be extended to perform globally considering all
the regions in US and the different kinds of Airbnb’s.














