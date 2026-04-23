# What Drives the Price of a Used Car?
### Practical Application II — CRISP-DM Framework

## Business Problem
A used car dealership wants to understand what factors drive the price of a used car. By identifying the key price drivers, the dealership can make better inventory decisions — stocking cars that consumers value and pricing them competitively.

## Research Question
**Which features most strongly predict the price of a used car, and what should a dealership prioritize when sourcing inventory?**

## Dataset
- **Source:** Kaggle used car listings dataset
- **Size:** ~426,000 records
- **Target Variable:** `price` (continuous, in USD)
- **Key Features:** year, odometer, manufacturer, condition, fuel, drive, type, title_status

> The dataset CSV is not included in this repository. Place `vehicles.csv` in a `data/` folder before running the notebook.

## Repository Structure
├── README.md
├── prompt_II.ipynb     # Main analysis notebook
## Models Compared
- Linear Regression (baseline)
- Ridge Regression (with GridSearchCV)
- Lasso Regression (with GridSearchCV)

## Evaluation Metric
**RMSE (Root Mean Squared Error)** was used as the primary metric because:
- It is expressed in dollars — directly interpretable for pricing decisions
- It penalizes large errors more heavily than MAE, which matters when mispricings cost real money
- **R²** is also reported to show how much price variance the model explains

## Results

### Model Performance

| Model | RMSE | R² |
|-------|------|----|
| Linear Regression | $3,264 | 0.8171 |
| Ridge Regression | $3,264 | 0.8171 |
| Lasso Regression | $3,265 | 0.8170 |

All three models perform similarly. **Ridge Regression is recommended** — it adds regularization to prevent overfitting without sacrificing accuracy, and its coefficients remain interpretable for business insight.

### Top Price Drivers (from Ridge coefficients)
1. **Vehicle Year** — strongest single predictor; newer cars command significantly higher prices
2. **Odometer Reading** — higher mileage strongly depresses price
3. **Condition** — "like new" and "excellent" fetch meaningful premiums over "good" or "fair"
4. **Drive Type** — 4WD/AWD vehicles price consistently higher than FWD
5. **Vehicle Type** — trucks and SUVs command the highest median prices
6. **Fuel Type** — diesel and electric vehicles command a premium
7. **Title Status** — salvage/rebuilt titles are heavily discounted vs clean title

## Key Recommendations for the Dealership

| Priority | Recommendation |
|----------|----------------|
| High | Stock **2015+ model year** vehicles — year is the top price driver |
| High | Prioritize **low-mileage (<50K miles)** inventory |
| High | Focus on **trucks and SUVs** — highest median prices |
| Medium | Invest in **reconditioning** — improving condition grade adds significant value |
| Medium | Source more **diesel and 4WD vehicles** for premium pricing |
| Lower | Avoid **salvage/rebuilt title** inventory unless deeply discounted |

## Methodology
1. **Data Understanding** — explored 426K listings, assessed missing values and distributions
2. **Data Cleaning** — filtered price ($500–$150K), year (1980–2023), dropped high-cardinality/low-utility columns
3. **Preprocessing** — median imputation + scaling for numerics; mode imputation + one-hot encoding for categoricals via sklearn Pipeline
4. **Modeling** — Linear, Ridge, and Lasso regression; Ridge/Lasso tuned with GridSearchCV (5-fold CV)
5. **Evaluation** — compared by RMSE and R²; Ridge coefficients interpreted for business recommendations

## Next Steps
- Test ensemble models (Random Forest, XGBoost) — likely to reduce RMSE significantly
- Incorporate geographic pricing — state-level variation was meaningful
- Build an internal pricing tool where staff input vehicle details and get a fair market estimate
- Add richer data: previous owners, service history, accident records

## Tools and Libraries
- Python 3, pandas, numpy, matplotlib, seaborn
- scikit-learn (Pipeline, ColumnTransformer, GridSearchCV, Ridge, Lasso)
