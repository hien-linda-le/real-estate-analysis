# Real Estate Analysis 🏠

The dataset “Realestate.csv” is a historical dataset of real estate valuation collected from a city in Taiwan. I received this dataset through Western Sydney University as part of practical coursework and exercises. All rights belong to the original data provider and the university materials from which it was supplied. It includes the following variables:
- age: the age of the house (in years)
- year: transaction year
- distanceMRT: the distance to the nearest metro rail transit (in meters)
- convstore: the number of convenience stores in the living circle on foot
- price: the house price of unit area (USD per square meter)

## 1. Introduction and Objectives

The analysis involves building Ordinary Least Squares (OLS) regression models to explore the relationship between a target variable (likely a property price) and a key predictor: distanceMRT. The objective was to test different model specifications, including linear, polynomial, and interaction effects, to find the best fit for the data.

## 2. Analysis Performed

### Model 1: summarise a simple linear regression analysis aimed at predicting the price of real estate based on its distance from the MRT.
- R-squared = 0.482: This means that 48.2% of the variability in the real estate price is explained by its distanceMRT.
- F-statistic: 381.9 with a near-zero p-value (1.28e-60). This indicates the model, as a whole, is statistically significant (i.e., distanceMRT is a significant predictor of price).
- Using the fitted model, the predicted price for a property located 500 meters from the MRT is 4071.55 (units of price).

### Model 2: a multiple linear regression analysis aimed at predicting real estate price using three predictor variables: age of the house, the year it was built, and the number of nearby convenience stores.
- R-squared = 0.435: This means that 43.5% of the variability in the real estate price is collectively explained by the three predictor variables age, year convvstore).
- Adjusted R^2 = 0.431: This slightly penalized R^2 accounts for the number of predictors, which is a better measure for comparing models.
- F-statistic: 105.1 with a near-zero p-value (1.82e-50). This indicates the overall model is highly statistically significant (at least one predictor is useful).

### Model 3: summarises the results of a reduced multiple linear regression model after removing the statistically insignificant variable (year) from the previous model. The goal is to create a more parsimonious model while maintaining predictive power.
- R-squared = 0.433.
- Adjusted R^2 = 0.431: R^2 dropped negligibly (from 0.435 to 0.433), and the Adjusted R^2 remained the same (0.431). This confirms that the year variable was not adding meaningful explanatory power to the model.
- F-statistic: 156.7 with a near-zero p-value (2.75e-51). The overall model remains highly statistically significant.

### Model 4: summarises a multiple linear regression model that includes an interaction term between distanceMRT and convstore to predict real estate price.
- R-squared: 0.619.
- Adjusted R^2 = 0.615: This is a major improvement over the previous models (SdistanceMRT at 0.480 and Reduced age/convstore at 0.431). The model now explains 61.5% of the variability in price.
- F-statistic: 165.8 with an extremely low p-value (3.95e-84). The overall model remains highly statistically significant.

### Model 5: summarises a polynomial regression model that attempts to fit a cubic (3rd-degree) curve to the relationship between real estate price and distanceMRT.
- R-squared = 0.588.
- Adjusted R^2: 0.585: This model is substantially better at explaining the variance in price than the initial simple linear models (R^2 < 0.5). It is second only to the interaction model (R^2 = 0.619) in overall explanatory power.
- F-statistic: 194.3 with a near-zero p-value (2.57e-78). The overall model is highly statistically significant, confirming that at least one power of distanceMRT is a significant predictor.

## 3. Final Interpretation Summary

- Distance to MRT affects price non-linearly.

- Properties close to MRT lose value very fast as you move away.

- The effect weakens around mid-distance.

- Very far out, prices still drop, but slowly.

- The polynomial model captures this, but with severe multicollinearity.

- The interaction model remains the strongest and most reliable.
