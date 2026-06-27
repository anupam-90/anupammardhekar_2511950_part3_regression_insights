# 1. Predicted Sales Calculation

The final Multiple Regression model, utilizing 11 predictors, serves as the basis for this residual analysis. The predicted monthly sales for each record were derived from the following regression equation:

*monthly_sales = 79,274.52 + 1.2003(marketing_spend) + 34.0034(footfall) − 45,730.96(avg_discount_pct) + 300,183.43(inventory_availability_pct) + 13,563.58(customer_rating) + 6,184.76(reg_North) + 18,678.42(reg_South) + 18,109.96(reg_West) + 12,786.00(type_Airport) − 11,002.40(type_HighStreet) − 29,091.73(type_Residential)*

**Note:** All calculated fitted values are located in the `MR_fitted` column of the "Predictions Residuals" sheet.

# 2. Residual Calculation

Residuals were computed to measure the deviation between observed and forecasted values:

*Residual = Actual monthly_sales − Predicted monthly_sales*

* **Positive Residual:** Indicates an under-prediction (Actual > Predicted).
* **Negative Residual:** Indicates an over-prediction (Actual < Predicted).

# 3. Residual analysis

### Records with the largest positive residuals:
* STR-1028: 112,722
* STR-1073: 106,193
* STR-1019: 92,631
* STR-1069: 91,669
* STR-1050: 89,536

### Records with the largest negative residuals:
* STR-1007: -112,680
* STR-1012: -119,858
* STR-1014: -99,952
* STR-1017: -159,545
* STR-1023: -145,888

**Positive Residual Analysis (Model Under-prediction):**
These outliers identify stores that significantly outperformed their predicted potential. For instance, STR-1028 (East region Mall store) exceeded expectations by over ₹112,000 in April 2025. Such performance spikes are often driven by external, unmeasured factors—such as local events, high-impact store management, or the sudden closure of a nearby competitor—that the current variable set does not account for.

**Negative Residual Analysis (Model Over-prediction):**
These records identify stores that underperformed relative to their characteristic profile. The largest gap, STR-1017 (West region High Street), fell short by ₹159,553. These significant variances often reflect localized operational disruptions, such as supply chain issues, regional economic headwinds, or aggressive competitor activity that remain exogenous to the model.

# 4. Under-prediction and Over-prediction by Store Type and Region

### Residual standard deviation by store type

| Store Type | Mean Residual | Std Dev | Min Residual | Max Residual |
| :--- | :---: | :---: | :---: | :---: |
| Airport | ≈ 0 | ₹39,928 | −₹70,603 | ₹74,568 |
| High Street | ≈ 0 | ₹40,318 | −₹159,553 | ₹91,656 |
| Mall | ≈ 0 | ₹45,280 | −₹145,874 | ₹112,716 |
| Residential | ≈ 0 | ₹44,192 | −₹119,865 | ₹106,199 |

### Residual standard deviation by region

| Region | Mean Residual | Std Dev | Min Residual | Max Residual |
| :--- | :---: | :---: | :---: | :---: |
| East | ≈ 0 | ₹43,090 | −₹80,681 | ₹112,716 |
| North | ≈ 0 | ₹38,026 | −₹99,070 | ₹89,551 |
| South | ≈ 0 | ₹43,683 | −₹145,874 | ₹76,303 |
| West | ≈ 0 | ₹44,742 | −₹159,553 | ₹91,656 |

### Key observations:

* **High Street Variability:** Displaying the widest residual range, the High Street model performance is likely constrained by hyperlocal factors (e.g., pedestrian traffic, proximity to transport) that the static dummy variables cannot capture.
* **Mall Performance:** Mall stores exhibit the highest residual standard deviation (₹45,280), suggesting high performance volatility likely linked to unique site characteristics like car park access or anchor tenant performance.
* **Regional Bias:** The West region shows the most significant negative residuals, indicating the current regional dummy variable may be over-estimating the baseline performance for specific stores in this locale.
* **Airport Consistency:** Airport stores demonstrate the tightest residual range, confirming that the model performs most reliably in the more standardized retail environment of an airport terminal.
* **Model Unbiasedness:** A mean residual near zero across all segments confirms that the model is balanced and free of systematic directional bias. However, the varying spreads indicate that future iterations could benefit from store-level fixed effects to further increase precision.
