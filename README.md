# Predicting Building Energy Usage for WiDS Datathon 2022
**Authors: Aisha Baitemirova-Othman, Emiko Naomasa**

## Objectives
Buildings accounted for 37% of global greenhouse gas emissions in 2020 ([IEA 2020](https://www.iea.org/reports/tracking-buildings-2021)). “Green building” is key to achieving the Paris Agreement goal. Policymakers and urban planners around the world employ various policy tools, such as building codes or financial incentives programs to retrofit, to improve the energy efficiency of buildings and construction sectors. For the program’s effective intervention, detailed data of energy consumption for each building is necessary. For example, many states in the U.S. mandate building energy disclosure, yet, it is still far from covering all buildings in the U.S. 

To fill this gap of building energy consumption data availability, we developed a prediction model of building energy consumption using data from the U.S., including building characteristics and climate and weather variables for the building's location. Our model provides granular energy usage predictions for each building. In addition, our prediction can support policymakers and urban planners in the U.S. to identify and prioritize a building in order to intervene and design necessary retrofitting programs without detailed building energy consumption data.

The model was submitted to a [Kaggle competition](https://www.kaggle.com/c/widsdatathon2022/overview/description) that WiDS Datathon 2022 hosts. 

## Data
The data set is provided through a Kaggle competition. Our target variable is the annual energy usage per square foot of a building, called **the site energy usage intensity (EUI)**. Our features include **building characteristics** (e.g., floor area, years of built, facility type) and **weather data for the building’s location** (e.g., annual average temperature, annual total precipitation, annual snowfalls). We received the training set with the target variable and the test set without the target variable. The test set is used for submission to the Kaggle competition. The training data has 75,757 observations covering 6 years from 7 states. The years and states are anonymized. 

The detailed list of features in our model is [here](https://www.kaggle.com/c/widsdatathon2022/data). 

For data cleaning and EDA, please read our notebooks.
- [Data Cleaning Notebook](https://github.com/eminaomasa/energy_usage_prediction/blob/main/DataCleaning.ipynb)
- [EDA Notebook](https://github.com/eminaomasa/energy_usage_prediction/blob/main/EDA.ipynb)

## Modeling
Considering this is the regression model, we evaluated ten machine learning algorithms to predict EUI. We used R2 scores to select the final model. 

1.	Dummy Regressor 
2.	Lasso Regression
3.	Ridge Regression
4.	Elastic Net
5.	Decision Tree 
6.	Random Forest
7.	Gradient Boosting (GBM)
8.	Light Gradient Boosting (Light GBM)
9.	Extreme Gradient Boosting (XGBM)
10.	Adaboost

To reduce the parameter turning time, we first checked each model’s R2 score in a default setting, and then for the top-performing models, we did hyperparameter tuning with a grid search. Following this method, we picked Light GBM as our final model (see Figure 1).  

For modeling, please read our notebooks.
- [Modeling Notebook](https://github.com/eminaomasa/energy_usage_prediction/blob/main/Modeling.ipynb)

## Model Validation
Figure 1 plots the R2 scores for ten models as well as the R2 score of our final model. Among ten models, Model 8 (Light GBM) apparently outperforms in terms of R2 scores. So, we chose the Light GBM as our candidate for the final model. After hyperparameter tuning, the Light GBM model’s R2 score increased from 0.5365 to 0.5995 (Final Model in Figure 1).  

**Figure 1: R2 score for ten models and our final model**

![image](https://user-images.githubusercontent.com/38669459/155844696-3d330c6b-b413-4b18-b53f-93237a946f02.png)

Moreover, our final model has a lower risk of overfitting, as the R2 score with the test data was 0.607, almost equal to the R2 score with the training data.

## Feature Analysis
Last, we examined the important features within our final model. Figure 2 displays the top 10 features according to importance. Floor area is the most important factor in determining a building’s energy use intensity. Energy star rating and year built are also important features. This finding is consistent with existing literature. In the meta review of building energy demand, [Ürge-Vorsatz et al. (2020)](https://www.annualreviews.org/doi/pdf/10.1146/annurev-environ-012420-045843) discussed that the floor area is one of the main drivers of energy consumption. [Kontokosta and Tull (2017)](https://www.sciencedirect.com/science/article/abs/pii/S0306261917303835) found that building age was a significant predictor of buildings’ energy use. 

**Figure 2**

![image](https://user-images.githubusercontent.com/38669459/155844782-3b5e27d2-2553-4d14-ab8b-4c41d1b80b32.png)



## Next Steps

## For Mode Information
For additional questions, please contact: [Aisha Baitemirova-Othman](https://www.linkedin.com/in/aishabaitemirovaothman/), [Emiko Naomasa](https://www.linkedin.com/in/emiko-naomasa-58782158/)

## Repository Structure

```
├── README.md                           
├── Data Cleaning.ipynb                             <- Data Cleaning Notebook
├── EDA.ipynb                                       <- EDA Notebook
├── Modeling.ipynb                                  <- Modeling Notebook
└── Data                                            <- Data downloaded from the kaggle competition
                           
```  
Note: Large or sensitive files are listed in .gitignore and not pushed to GitHub. 



