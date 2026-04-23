[What Drives the Price of a Used Car?
Practical Application II
---
Summary of Findings
This project analyzes a dataset of 426,000 used car listings to identify the key factors that drive used car prices. Using the CRISP-DM framework, we built and compared three regression models (Linear Regression, Ridge, and Lasso) to predict price and extract actionable insights for a used car dealership.
Top Price Drivers (in order of importance)
Vehicle Year — Newer cars command significantly higher prices; the strongest single predictor
Odometer Reading — Higher mileage strongly depresses price
Condition — "Like new" and "excellent" condition vehicles fetch meaningful premiums
Drive Type — 4WD/AWD vehicles price higher than FWD, especially in northern states
Vehicle Type — Trucks and SUVs consistently outsell sedans on price
Fuel Type — Diesel and electric vehicles command a premium
Title Status — Clean title is essential; salvage/rebuilt titles are heavily discounted
Key Recommendations for the Dealership
Stock 2015+ model year, low-mileage (<50K miles) vehicles
Prioritize trucks and SUVs over sedans and hatchbacks
Invest in reconditioning to improve condition grades before listing
Source more 4WD/diesel vehicles for premium pricing
Avoid salvage/rebuilt title inventory
---


Technologies Used
Python 3
pandas, numpy
matplotlib, seaborn
scikit-learn (Pipeline, ColumnTransformer, GridSearchCV, Ridge, Lasso)
---
Evaluation Metric
RMSE (Root Mean Squared Error) was used as the primary metric because it is expressed in dollars (interpretable) and penalizes large prediction errors more heavily — important for a real-world pricing application.
](https://github.com/SoumyaP-bit/used-car-price-analysis)
