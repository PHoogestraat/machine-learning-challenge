# Machine Learning Homework - Exoplanet Exploration

![exoplanets.jpg](Images/exoplanets.jpg)


## Background

The Kepler Space Observatory is a NASA-build satellite that was launched in 2009. The telescope is dedicated to searching for exoplanets in star systems besides our own, with the ultimate goal of possibly finding other habitable planets besides our own. The original mission ended in 2013 due to mechanical failures, but the telescope has nevertheless been functional since 2014 on a "K2" extended mission.

Kepler had verified 1284 new exoplanets as of May 2016. As of October 2017 there are over 3000 confirmed exoplanets total (using all detection methods, including ground-based ones). The telescope is still active and continues to collect new data on its extended mission.

To process this data, three machine learning models capable of classifying candidate exoplanets from the raw dataset were created. This process was exacuted in the following stages:

1. [Preprocess the data](#Preprocessing)
2. [Models](#Models)
3. [Review](#Review)

- - -

## Stages

### Preprocess the Data
Data was optained from the [Exoplanet Data Source](https://www.kaggle.com/nasa/kepler-exoplanet-search-results) located on kaggle and evaluated. Initial data set was 3.5 Mb containing 50 categories (columns) of data representing 10,000 exoplanet candidates Kepler has taken observations on. Null values were removed. The koi_disposition category (CANDIDATE, FALSE POSITIVE, NOT DISPOSITIONED or CONFIRMED) was converted to categorical (y) data type using hot-encoding. A random forest algorithm (python program: ml_find_features.ipynb) was employed on the modified data set to identify the top ten features impacting koi_dispositon.  A  dataset composed of the koi_dispositon and the ten most important features was created and served as the primary dataset for developing models (dataset: Top_10_origianl_koi_dispositon_data.csv). An additional dataset was created on the same dataset using MinMaxScaler as an additional resource.

### Models

Three models were created to explore the dataset (model_1_Random_Forest_Decision_Tree.ipynb, model_2_SVC_Grid_Search, and model_3_Neural_network_Keras.ipynb).  Each model employed the primary dataset described above. The Random Forest Decision Tree Model had a testing data score of 0.89 and a training Data score of 1.0 with the primary dataset. The SVC model tuned with Grid Search had a testing data score of 0.88 and a training Data score of 0.89 with the primary dataset. After employing Grid Search the best score was 0.86. The Neural Networks with Keras model had a testing data score of 0.88 with the primary dataset. Each model was saved under the prefix z#_  after completion.

* Random Forest model Score:        0.89
* SVC Model with GridSearh Score:   0.88
* Neural Netwroks Score:            0.88

### Review

 
Additional analysis of each mode was conducted. Precision data was also evaluated with respect to  koi_disposition ( Candidate, Confirmed, False Positive) for the Random Forest and SVC models. The False Positive disposition for these models was considerably higher than the other categories (Random Forest = 0.98, SVC =0.96). The Candidate disposition was: Random Forest = 0.80, SVC =0.83. The Confirmed disposition:  Random Forest = 0.79, SVC =0.78. These values appear to be the same. Values for the Neural Netwroks Score were not obtained. 

|Model|koi disposition|Score|recall|f1-score|Support|
|-----|---------------|-----|------|--------|-------|
|Random Forest|False Positive|0.98|0.73|0.77|411|
|SVC|False Positive|0.96|0.98|0.97|853|
|Random Forest|Candidate|0.80|0.73|0.77|411|
|SVC|Candidate|0.83|0.69|0.75|411|
|Random Forest|Confirmed CANDIDATE|0.79|0.83| 0.81|484|
|SVC|Confirmed CANDIDATE|0.78|0.86|0.82|484|


- - -

## Resources

* [Exoplanet Data Source](https://www.kaggle.com/nasa/kepler-exoplanet-search-results)

* [Scikit-Learn Tutorial Part 1](https://www.youtube.com/watch?v=4PXAztQtoTg)

* [Scikit-Learn Tutorial Part 2](https://www.youtube.com/watch?v=gK43gtGh49o&t=5858s)

* [Grid Search](https://scikit-learn.org/stable/modules/grid_search.html)

- - -



- - -





