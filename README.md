# DSI_Project_2

----------------
## Problem Statement:

- Where do we see benefits to a home's value? Where does Ames IA stand out and how does out study of homes in Ames help us find the3se benefits elsewhere?

----------------
## Methods & Sources:
- This analysis was conducted using a combination of multiple regression methods.
- The departure for the analysis was OLS regression with the results of this model compared against Lasso and Ridge models.
- ScikitLearn's corresponding modules were utilized for model production.
- Hyperparamaters were adjusted manually for the Lasso and Ridge models, with results evaluated ad-hoc.
- The training and testing data for this analysis was divided between two separate files.
- The training data source is the Ames housing data set compiled from the respective county assessor's office.
- Initial features from this dataset consisted of continuous, discrete, ordinal, and nominal types.
- The associated Data Dictionary is linked to here for ease of reference:
---link---
- The testing data is of unknown origin for the purposes of modeling.
- The testing data was put through the same preprocessing sequence as the training data in advance of transformation and model prediction.
----------------

## Initial Cleaning & Organization
- Null values were filled with guidance from the provided Data Dictionary.
- An observed house that lacked a given feature was designated at '0' for the feature.
- Ordinal features were ranked beginning at 1 with 1 being the 'best'.  This required reversing the orginal ranks for a few features.  This was done for ease of comparison among ranked features.
- Two features related to the presence of a swimming pool were dropped as they were composed of mostly null values.
- One hot encoding was applied to all nominal features.
- Some encoded features were not shared between the training and testing datasets. These features were regretably ignored in the interest of time.
----------------

## EDA
- One dimensional heatmaps were constructed to identify correlations with the target feature.
- Scatterplots were utilized for continuous features.
- Histograms were used for ordinal features with the x-axis corresponding to the ranking.
- Boxplots were utilized to identify categorical features with many outliers or no outliers.
- A particular feature, 'Year Built' was often not considered for modeling as it is likely significantly colinear with other explanatory features. 
-----------------

## Modeling
- Different combinations of features were selected.
- One combination was selected from the features that had the strongest correlaitons with the target as seen from the heatmaps.
- General experiments were done selecting features of a given type (ordinal, continuous, etc.)
- Features were also selected in groups that could be scaled or not scaled in unison.
- Some of the groups of features that were scaled were also modeled without scaling.
- The feature combination that delivered the best score for Kaggle was not intuitive for answering the problem statement. This initial limitation had an advantage in that more trial and error experiments could be done for the submissions.
- OLS, Lasso and Ridge models were utilized for comparison.
- Hyperparameters for Lasso and Ridge were adjusted for fine-tuning.
- Slight possible heteroskedasticity was detected from scatterplots.
- The model errors did appear to follow an approximately normal distribution.
------------------

## Results
- Satisfactory results were provided by a scaled set of 32 continuous and discreet features.
- The scores are presented rounded to two decimal places.

- The OLS model:--
  Train r2: .78
  Test r2: .82
  Train CVS: .77
  Test CVS: .77
  RMSE: 32861.56
  
  Strongly Positive Coefficients:--
  - Year Built: 11652.5
  - Year Remod/Add: 11755.6
  - Garage Cars: 9430.95
  - Bsmt Full Bath: 6128.27
  - Garage Area: 6270.66
  - Fireplaces: 6859.95
  - Screen Porch: 6209.03

  Strongly Negative Coefficients:--
  - Bedroom AbvGr: -7368.15
  - Pool Area: -6771.63
  - Garage Yr Blt: -4854.65
  
- The Ridge Model:--
  Train r2: .78
  Test r2: .82
  Train CV: .78
  Test CV: .82
  
  Strongly Positive Coefficients:--
  - Year Built: 11534.6
  - Year Remod/Add: 11778.4
  - Garage Cars: 9262.15
  - Bsmt Full Bath: 6145.06
  - Garage Area: 6412.74
  - Fireplaces: 6865.14
  - Screen Porch: 6175.93

  Strongly Negative Coefficients:--
  - Bedroom AbvGr: -7174.18
  - Pool Area: -6697.25
  - Garage Yr Blt: -4718.49
  
- The Lasso Model:--
  Train r2: .78
  Test r2: .82
  Train CV: .78
  Test CV: .82
  
  Strongly Positive Coefficients:--
  - Fireplaces: 10754.3
  - TotRms AbvGrd: 6628.49
  - Year Remod/Add: 11778.4
  - Bsmt Full Bath: 11721.8
  - Full Bath: 4280.11

  Strongly Negative Coefficients:--
  - Kitchen AbvGr: -39417.8
  - Bedroom AbvGr: -8925.3
  - Half Bath: -3030.39
  
- All models returned almost identical r2 scores even with reasonably large adjustments to hyperparameters.
- The Lasso model attributed stronger influence to a different group of coefficients.
-----------------

## Conclusions:
- One hot encoded variables were difficult to interpret as many had very limited observations.
- The highest score submitted to Kaggle was produced by all features (original and engineered) from data that was not scaled.
- This score in particulay may not by reliable until further analysis is done.
- Next steps would be including hypothesis tests and more thorough tests for linear assumptions to validate these results.
  
