Business Case Analysis

Scenario: Promotion Effectiveness at a Fashion Retail Chain

---

B1. Problem Formulation

(a)

The target variable is items_sold, as the objective is to maximise the number of items sold.

Candidate input features include:

- Promotion type
- Store size
- Location type (urban, semi-urban, rural)
- Competition density
- Customer demographics
- Time-based features (month, weekend, festival)

This is a supervised regression problem, because the target variable is continuous and we aim to predict its value based on input features.

---

(b)

Using items_sold is more reliable than revenue because revenue can be influenced by pricing, discounts, and external economic factors, whereas items_sold directly reflects customer demand.

This illustrates that the target variable should closely align with the business objective and avoid unnecessary noise.

---

(c)

Instead of using a single global model, a better approach would be:

- Building separate models for different store segments (e.g., urban vs rural), or
- Including store/location features in the model

This helps capture differences in customer behavior across regions and improves model performance.

---

B2. Data and EDA Strategy

(a)

The final dataset should have one row per store per month.

Data sources would be joined as follows:

- Transactions → aggregated to monthly store-level sales
- Store attributes → joined using store_id
- Promotion details → joined by promotion and time
- Calendar → joined using date (weekend/festival flags)

Aggregations:

- Total items_sold per store per month
- Average basket size
- Monthly footfall

---

(b)

EDA steps include:

1. Histogram plots
   To understand the distribution of numerical features like items_sold.

2. Boxplots by promotion type
   To compare the effectiveness of different promotions.

3. Time series plots
   To identify trends and seasonality in sales.

4. Correlation heatmap
   To understand relationships between numerical variables.

These analyses help in feature engineering and model selection.

---

(c)

Since 80% of transactions occur without promotions, the dataset is imbalanced.

This may bias the model towards non-promotion cases.

To address this:

- Use stratified sampling
- Apply weighting techniques
- Evaluate performance separately for promotion vs non-promotion

---

B3. Model Evaluation and Deployment

(a)

A time-based train-test split should be used, where past data is used for training and recent data for testing.

A random split is inappropriate because it can cause data leakage in time-based datasets.

Evaluation metrics:

- RMSE: measures overall error and penalizes large mistakes
- MAE: measures average error and is easier to interpret

Lower values indicate better model performance.

---

(b)

Different recommendations for the same store in different months occur due to changing conditions.

For example:

- In December, festivals may increase the effectiveness of loyalty-based promotions
- In other months, discounts may perform better

Feature importance or SHAP values can help explain how different factors influence predictions over time.

---

(c)

Deployment process:

1. Save the trained model using joblib or pickle
2. Collect new monthly data
3. Apply the same preprocessing pipeline
4. Generate predictions for each store
5. Monitor performance using RMSE/MAE

If performance drops, retrain the model with updated data.

---

Conclusion

Machine learning helps optimize promotion strategies by predicting sales and identifying key factors influencing customer behavior. This enables better decision-making and improved business performance.
