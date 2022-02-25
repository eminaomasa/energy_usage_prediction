# Predicting Building Energy Usage for WiDS Datathon 2022
**Authors: Aisha Baitemirova-Othman, Emiko Naomasa**

## Objectives:
Buildings accounted for 37% of global greenhouse gas emissions in 2020 ([IEA 2020](https://www.iea.org/reports/tracking-buildings-2021)). “Green building” is key to achieving the Paris Agreement goal. Policymakers and urban planners around the world employ various policy tools, such as building codes or financial incentives programs to retrofit, to improve the energy efficiency of buildings and construction sectors. For the program’s effective intervention, detailed data of energy consumption for each building is necessary. For example, many states in the U.S. mandate building energy disclosure, yet, it is still far from covering all buildings in the U.S. 

To fill this gap of building energy consumption data availability, we developed a prediction model of building energy consumption using data from the U.S., including building characteristics and climate and weather variables for the building's location. Our model provides granular energy usage predictions for each building. In addition, our prediction can support policymakers and urban planners in the U.S. to identify and prioritize a building in order to intervene and design necessary retrofitting programs without detailed building energy consumption data.

The model was submitted to a [Kaggle competition](https://www.kaggle.com/c/widsdatathon2022/overview/description) that WiDS Datathon 2022 hosts. 

## Data:
The data set is provided through a Kaggle competition. Our target variable is the annual energy usage per square foot of a building, called **the site energy usage intensity (EUI)**. Our features include **building characteristics** (e.g., floor area, years of built, facility type) and **weather data for the building’s location** (e.g., annual average temperature, annual total precipitation, annual snowfalls). We received the training set with the target variable and the test set without the target variable. The test set is used for submission to the Kaggle competition. The training data has 75,757 observations covering 6 years from 7 states. The years and states are anonymized. 

The detailed list of features in our model is [here](https://www.kaggle.com/c/widsdatathon2022/data). 

For data cleaning and EDA, please read our notebooks.
- [Data Cleaning Notebook](add link)
- [EDA Notebook](https://github.com/eminaomasa/energy_usage_prediction/blob/main/EDA.ipynb)

## Modeling: 
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

**Figure 1: R2 scores for 10 models**

Here, add bar graph plotting R2 for 10 models.  

For modeling, please read our notebooks.
- [Modeling Notebook](add link)

## Model Validation:


## Next Steps:

## For Mode Information
For additional questions, please contact: [Aisha Baitemirova-Othman](https://www.linkedin.com/in/aishabaitemirovaothman/), [Emiko Naomasa](https://www.linkedin.com/in/emiko-naomasa-58782158/)

## Repository Structure

```
├── README.md                           
├── Data Cleaning.ipynb                             <- Data Cleaning Notebook
├── EDA.ipynb                                       <- EDA Notebook
├── Modeling.ipynb                                  <- Modeling Notebook for Model 1
└── Data                                            <- Data downloaded from the kaggle competition
                           
```  
Note: Large or sensitive files are listed in .gitignore and not pushed to GitHub. 



