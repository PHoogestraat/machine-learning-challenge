# Machine Learning Homework - Exoplanet Exploration

![exoplanets.jpg](Images/exoplanets.jpg)


## Background

The Kepler Space Observatory is a NASA-build satellite that was launched in 2009. The telescope is dedicated to searching for exoplanets in star systems besides our own, with the ultimate goal of possibly finding other habitable planets besides our own. The original mission ended in 2013 due to mechanical failures, but the telescope has nevertheless been functional since 2014 on a "K2" extended mission.

Kepler had verified 1284 new exoplanets as of May 2016. As of October 2017 there are over 3000 confirmed exoplanets total (using all detection methods, including ground-based ones). The telescope is still active and continues to collect new data on its extended mission.

To process this data, three machine learning models capable of classifying candidate exoplanets from the raw dataset were created. This process was exacuted in the following stages:

1. [Preprocess the raw data](#Preprocessing)
2. [Models](#Models)
3. [Reporitng](#Reporting)

- - -

## Stages

### Preprocess the Data
Data was optained from the [Exoplanet Data Source](https://www.kaggle.com/nasa/kepler-exoplanet-search-results) located on kaggle and evaluated. Initial data set was 3.5 Mb containing 50 categories (columns) of data representing 10,000 exoplanet candidates Kepler has taken observations on. Null values were removed. The koi_disposition category (CANDIDATE, FALSE POSITIVE, NOT DISPOSITIONED or CONFIRMED) was converted to categorical (y) data type using hot-encoding. A random forest algorithm (python program: ml_find_features.ipynb) was employed on the modified data set to identify the top ten features impacting koi_dispositon.  A  dataset composed of the koi_dispositon and the ten most important features was created and served as the primary dataset for developing models (dataset: Top_10_origianl_koi_dispositon_data.csv). An additional dataset was created on the same dataset using MinMaxScaler as an additional resource.

### Models

Three models were created to explore the dataset (model_1_Random_Forest_Decision_Tree.ipynb, model_2_SVC_Grid_Search, and model_3_Neural_network_Keras.ipynb).  Each model employed the primary dataset described above. The Random Forest Decision Tree Model had a testing data score of 0.89 and a training Data score of 1.0 with the primary dataset. The SVC model tuned with Grid Search had a testing data score of 0.88 and a training Data score of 0.89 with the primary dataset. After employing Grid Search the best score was 0.86. The Neural Networks with Keras model had a testing data score of 0.88 with the primary dataset.

### Reporting

* Create a README that reports a comparison of each model's performance as well as a summary about your findings and any assumptions you can make based on your model (is your model good enough to predict new exoplanets? Why or why not? What would make your model be better at predicting new exoplanets?).

- - -

## Resources

* [Exoplanet Data Source](https://www.kaggle.com/nasa/kepler-exoplanet-search-results)

* [Scikit-Learn Tutorial Part 1](https://www.youtube.com/watch?v=4PXAztQtoTg)

* [Scikit-Learn Tutorial Part 2](https://www.youtube.com/watch?v=gK43gtGh49o&t=5858s)

* [Grid Search](https://scikit-learn.org/stable/modules/grid_search.html)

- - -



- - -

## Submission




