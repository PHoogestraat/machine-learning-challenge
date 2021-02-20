# Machine Learning Homework - Exoplanet Exploration

![exoplanets.jpg](Images/exoplanets.jpg)


## Background

The Kepler Space Observatory is a NASA-build satellite launched in 2009. The telescope is searching for exoplanets in star systems outside of our own. The ultimate goal of the satelite is to identify habitable planets. The original mission ended in 2013 due to mechanical failures, but the telescope has nevertheless been functional since 2014 on a "K2" extended mission.

Kepler had verified 1284 new exoplanets as of May 2016. As of October 2017 there are over 3000 confirmed exoplanets total (using all detection methods, including ground-based ones). The telescope is still active and continues to collect new data on its extended mission.

## Goal
Create a machine learning model capable of classifying candidate exoplanets with greater than 85% model score using data created by the Kepler Space Observatory. This process was exacuted in the following stages:

1. [Preprocess the data](#Preprocessing)
2. [Models](#Models)
3. [Review](#Review)

- - -

## Stages

### Preprocess the Data
Data was obtained from the [Exoplanet Data Source](https://www.kaggle.com/nasa/kepler-exoplanet-search-results) located on Kaggle. Initial dataset was 3.5 Mb containing 50 categories (columns) of data representing 10,000 exoplanet candidates Kepler has made observations on. Null values were removed. The koi_disposition category (CANDIDATE, FALSE POSITIVE, NOT DISPOSITIONED or CONFIRMED) was converted to categorical data type (y) using hot-encoding. A random forest algorithm (python program: ml_find_features.ipynb) was employed to identify the top ten features impacting koi_dispositon. A dataset composed of the koi_dispositon and the ten most important features was created and served as the primary dataset for developing models (dataset: Top_10_origianl_koi_dispositon_data.csv). An additional dataset was created on the same dataset using MinMaxScaler as an additional resource.

### Models

A Random Forest, SVC (with GridSearch), and Neural Network models were created to identify exoplanets identified by the Kepler Space Observatory. Each model employed the primary dataset described above. In addition to the primary data set, an additional Random Forest model was created using the dataset generated from the MinMaxScaler. This model did not show a significant difference and was not reported.  The SVC model was optimized by using a rbf kernel. GridSearch was also employed to further tune the model. The optimized parameters were: C, 50, gamma, and 0.0005. The Neural Networks model employed Keras. A MinMaxScaler function was also used in preprocessing the data. Each model was saved under the prefix z#_  after completion.

### Review
Analysis of each mode was conducted and reported below. 

|Model|Model Score|Training Score|
|-----|-----------|--------------|
|Random Forest  |0.89|1.0 |
|SVC(GridSearh Score)|  0.88|0.89|
|Neural Network|  0.88|N.A.|


Additional analysis of each mode was conducted. Precision data was also evaluated with respect to  koi_disposition ( Candidate, Confirmed, False Positive) for the Random Forest and SVC models. The coresponding values for the Neural Netwroks Score were not obtained. 

|Model|koi disposition|Score|recall|f1-score|Support|
|-----|---------------|-----|------|--------|-------|
|Random Forest|False Positive|0.98|0.73|0.77|411|
|SVC|False Positive|0.96|0.98|0.97|853|
|Random Forest|Candidate|0.80|0.73|0.77|411|
|SVC|Candidate|0.83|0.69|0.75|411|
|Random Forest|Confirmed CANDIDATE|0.79|0.83| 0.81|484|
|SVC|Confirmed CANDIDATE|0.78|0.86|0.82|484|

## Conclusion
All three models performed approximately the same. The Random Forest model did have a significantly higher training score value. The Random Forest model also is convenient to use which may make it the best candidate. However, there are no real distinguishing differences between the models in predicting exoplanets.

- - -

## Resources

* [Exoplanet Data Source](https://www.kaggle.com/nasa/kepler-exoplanet-search-results)

* [Scikit-Learn Tutorial Part 1](https://www.youtube.com/watch?v=4PXAztQtoTg)

* [Scikit-Learn Tutorial Part 2](https://www.youtube.com/watch?v=gK43gtGh49o&t=5858s)

* [Grid Search](https://scikit-learn.org/stable/modules/grid_search.html)

- - -



- - -





