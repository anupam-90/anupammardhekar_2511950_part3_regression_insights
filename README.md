# Store Performance Regression Analysis

## Business problem summary:
This initiative utilizes multiple linear regression to identify and quantify the primary drivers of retail store performance. To optimize operations, management requires a data-driven understanding of the specific locational and operational factors that impact monthly revenue. 

*This analysis addresses the core business question:* Which variables reliably predict monthly sales across our retail footprint, and what proportion of revenue variance is explained by observable store characteristics? These findings are designed to provide a framework for strategic decision-making regarding marketing budgets, inventory management, customer service initiatives, and location-based resource allocation.

## Dataset Description

The dataset comprises 320 observations, capturing monthly performance metrics across various retail locations from January 2025 to April 2025.

### 1. Dependent Variable (Target)
* `monthly_sales`: The primary continuous numerical metric utilized as the target for regression modeling.
    * Note: `monthly_profit` is excluded from the primary sales regression to eliminate the risk of target leakage and ensure model integrity.

### 2. Potential Independent Variables (Predictors)
* Numerical Predictors:
    * `marketing_spend`: Continuous (₹) — Expected to have a positive correlation with sales.
    * `footfall`: Discrete count — Anticipated as a primary driver of transaction volume.
    * `avg_discount_pct`: Continuous (%) — Influences both transaction volume and average ticket size.
    * `staff_count`: Discrete count — Serves as a proxy for operational capacity and service levels.
    * `inventory_availability_pct`: Continuous (%) — Measures the ability to satisfy consumer demand.
    * `competitor_distance_km`: Continuous (km) — Indicates market saturation and external competition.
    * `customer_rating`: Continuous (1-5 scale) — Quantifies customer sentiment and satisfaction.
* Categorical Predictors:
    * `region`: Nominal (East, West, North, South).
    * `store_type`: Nominal (Mall, High Street, Residential, Airport).
* Binary Indicator:
    * `holiday_flag`: Binary (0 or 1) — Captures seasonal demand spikes.

### 3. Variables Needing Cleaning or Transformation
* `avg_discount_pct` & `inventory_availability_pct`: Standardized to decimal format (e.g., `0.15` and `0.85`) to ensure consistency across calculations.
* `month`: Converted from raw date formats into categorical or seasonal blocks to prevent interpretation errors by the regression engine.
* Missing Data Imputation: Missing values in `customer_rating` and `competitor_distance_km` were filled using respective column averages (mean rating: 3.92; mean distance: 8.67 km) to maintain sample size and mitigate deletion bias.

### 4. Regression Approach
Three distinct models were constructed to evaluate performance:

* **SR1 (Simple Regression 1):** Regresses `monthly_sales` on `marketing_spend` to establish a baseline for marketing ROI.
* **SR2 (Simple Regression 2):** Regresses `monthly_sales` on `footfall` to evaluate the predictive strength of physical traffic.
* **MR (Multiple Regression):** Regresses `monthly_sales` on all 11 independent variables, incorporating both numerical predictors and dummy variables. This serves as the primary, final model.

*All models were executed via the Excel Data Analysis ToolPak; residuals and fitted values were archived for diagnostic validation.* ### 5. Variables Not Useful for Regression
* **`store_id`**: A high-cardinality primary key lacking predictive utility for generalized modeling.
* **`monthly_profit`**: Excluded to avoid logical endogeneity, as profit is mathematically derived from sales and costs.

### 6. Dummy Variable approach: 
Categorical variables were converted to binary format to ensure model compatibility:

* **Region:** Dummies (reg_North, reg_South, reg_West) were created, with East acting as the baseline.
* **Store Type:** Dummies (type_Airport, type_HighStreet, type_Residential) were created, with Mall acting as the baseline.

*This approach prevents the dummy variable trap and ensures the model avoids perfect multicollinearity.*

## 7. Model Comparison Summary

| Metric | SR1 (marketing_spend) | SR2 (footfall) | MR (all variables) |
|:---|:---:|:---:|:---:|
| R-squared | 0.1672 | 0.7363 | 0.8320 |
| Adjusted R-squared | 0.1646 | 0.7355 | 0.8260 |
| F-statistic | 63.8649 | 887.8488 | 138.6813 |
| Significance F | 2.48E-14 | 4.75E-94 | 3.12E-112 |
| SSE | 2.86E+12 | 9.06E+11 | 5.77E+11 |
| Standard Error | ₹94,846 | ₹53,374 | ₹43,285 |
| Overall Significant? | Yes | Yes | Yes |
| Preferred Model? | No | No | Yes |

## 8. Final Model Selected

The Multiple Regression (MR) model was chosen as the optimal solution due to:
- Superior explanatory power, with an $R^2$ of 0.8320.
- Minimal prediction error, evidenced by the lowest SSE (5.77 × 10¹¹) and a standard error of ₹43,285.
- Strong statistical significance, with 7 of 11 predictors achieving p < 0.05.

*Non-significant predictors were retained to maintain documentation integrity and reflect a comprehensive model view.*

## 9. Business Recommendation

* **Maximize Footfall:** With a coefficient of ₹34.00 per visitor, traffic-driving initiatives remain the highest priority for revenue growth.
* **Optimize Marketing Spend:** A return of ₹1.20 per ₹1 invested provides a clear benchmark for budget maintenance.
* **Ensure Stock Availability:** A 10 percentage point increase in availability correlates to ~₹30,018 in additional monthly sales; supply chain efficiency is critical.
* **Leverage CX Metrics:** Each one-point improvement in customer rating yields ₹13,548; prioritize staff training and service quality.
* **Differentiate Targets:** Address the structural performance gap of Residential stores (underperforming Mall stores by ₹29,092) by adjusting sales targets accordingly.
* **Regional Optimization:** Investigate the operational strategies of high-performing South and West stores for potential replication.

## 10. Assumptions and Limitations

**Assumptions:**
- Linearity between independent variables and `monthly_sales`.
- Normal distribution of residuals with a mean centered at zero.
- Absence of perfect multicollinearity between independent variables.
- Independence of store-month observations.

**Limitations:**
- Temporal scope: The four-month window (Jan–Apr 2025) precludes the identification of long-term seasonality.
- Correlation vs. Causality: Regression results identify association; intervention impacts should be tested via controlled experiments.
- Omitted Variables: The model does not account for localized competitor activity, macroeconomic shifts, or management quality, which likely account for the remaining 16.8% of variance.

## 11. Screenshots Included

1. `simple_regression_output.png`
2. `multiple_regression_output.png`
3. `model_comparison_preview.png`
