![cover](./images/spotify_cover.jpg)

[Image](https://www.edmsauce.com/wp-content/uploads/2017/01/6360041936368655181636978495_shutterstock_200035424.jpg)

# What's Spoppin'?

#### Author: Erin Vu

## Overview

This project is an analysis and prediction of popularity of Spotify tracks from the Kaggle datset in order to provide music production companies with a good idea of the attributes of popular songs. As a result of iterating through linear regression and random forest regression models, the most impactful feature through random forest regression was instrumentalness, duration, and acousticness, and can recommend to have produce songs with a mix of vocals and instruments.

## Business Problem 

The business problem for our music production companies and producers, our stakeholders, is making popular songs and figuring out what attributes make a popular song. Music production companies and producers need to know generally what people like to listen to, and with this project we can find those optimal features. We will be using linear regression and random forest regression to predict popularity of songs based on the feature data. With this information, production companies will be able to produce new popular songs to build artists' profile, and fame.

## Data 

The [Spotfy dataset from Kaggle](https://www.kaggle.com/yamaerenay/spotify-dataset-19212020-160k-tracks) has almost 600,000 songs from the years 1922-2021, and has 20 columns. The target variable is Popularity and the other features wil be used to predict the target variable. The variables are listed below as they were in the dataset description set on Kaggle and the main predictor variables for this will be the numerical features such as acousticness, danceability, energy, etc. These variables are relevant because the combinations are unique to each song and makes up a population score. A limitation for predicting popularity with this datset is predicting popularity for different age groups and user tastes as the dataset has a wide range of songs and people like different sounds and enjoy different sounds in different time periods.

To follow along with this repository, please fork this repository, and download the dataset from Kaggle into the /data folder.

#### Primary:

id (Id of track generated by Spotify)

#### Numerical:

acousticness (Ranges from 0 to 1)

danceability (Ranges from 0 to 1)

energy (Ranges from 0 to 1)

duration_ms (Integer typically ranging from 200k to 300k)

instrumentalness (Ranges from 0 to 1)

valence (Ranges from 0 to 1)

popularity (Ranges from 0 to 100)

tempo (Float typically ranging from 50 to 150)

liveness (Ranges from 0 to 1)

loudness (Float typically ranging from -60 to 0)

speechiness (Ranges from 0 to 1)

#### Dummy:

mode (0 = Minor, 1 = Major)

explicit (0 = No explicit content, 1 = Explicit content)

#### Categorical:

key (All keys on octave encoded as values ranging from 0 to 11, starting on C as 0, C# as 1 and so on…)

timesignature (The predicted timesignature, most typically 4)

artists (List of artists mentioned)

artists (Ids of mentioned artists)

release_date (Date of release mostly in yyyy-mm-dd format, however precision of date may vary)

name (Name of the song)

Below is the distribution of our target variable, popularity.

![pop_dist](./images/pop_dist.png)


Below we can observe the correlations of the features with our target.


![pop_heat](./images/heatmap.png)


## Methods

By using Python and its packages such as numpy and pandas, we explored the data's features and their relationship to our target variable, popularity. After exploration, we used other libraries such as scikit-learn and xgboost to model our predictions. Within scikit-learn, we iterated through linear regression and random forest regression models to predict popularity. We then used xgboost to further explore other models that might improve our score. The metric used to evaluate the models were the RMSE score. The R2 score was also observed.

## Results

Our evaluation metric in this project was mainly the RMSE score while also observing the r2 score. The RMSE score is a measure of the square root the mean squared error, which measures the average of the distances between the actual popularity and the predicted popularity. The goal for this project is to minimize that distance. The r2 score tells us what % of the variance is explained by the model and we try to get this value as high as possible. The RMSE scores for our linear regression models were almost the same, indicating that the training and test predictions performed roughly the same. The decision tree model also performed roughly the same on the training and validation set. The random forest regression model and the XGBoost models performed poorly on the validation set, indicating those models were overfit. Although the models were overfit, they still performed better than our baseline model. With these results, we are somewhat confident in our best model, the XGBoost model, and its ability generalize and predict popularity.

![rmse](./images/rmse_scores.png)


![r2](./images/r2_scores.png)

Below we can see the feature importances extracted from the random forest regression model.

![feat_impt_with](./images/ft_impt_with_artists.png)


## Conclusions

As a result of this project, I believe we can recommend music production studios to make new songs with popular artists and to make the songs lean on the side of mixing in vocals with instruments. Some reasons why this analysis might not fully solve the problem is due to the size of the data and the parameter tuning of the model. Subsetting the data by years and dividing it out into different genre models will most likely lead to better predictions, which is also a next step for improvement on the project.

## For More Information

Please review the full analysis in the [Jupyter Notebook](https://github.com/ekvu/whats_spoppin/blob/main/final.ipynb) or the [presentation](https://github.com/ekvu/whats_spoppin/blob/main/final_presentation.pdf). For any additional questions, please contact me at erin_vu@pm.me.

## Repository Structure

```
├── README.md                         
├── pickle
├── final.ipynb
├── final_presentation.pdf        
├── data                                
├── images     
└── working_notebook
```
