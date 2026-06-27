# Regression Model Comparison

## Overview 
This analysis evaluates three regression models developed to forecast `monthly_sales` across 320 distinct retail store observations. The following comparison highlights model performance, identifies key predictors, and discusses practical business implications and inherent limitations.

| Metric | SR1 (marketing_spend) | SR2 (footfall) | MR (all variables) |
|---|:---:|:---:|:---:|
| Dependent Variable | monthly_sales | monthly_sales | monthly_sales |
| Independent Variables | marketing_spend | footfall | marketing_spend, footfall, avg_discount_pct, inventory_availability_decimal, customer_rating, region_North, region_South, region_West, type_Airport, type_HighStreet, type_Residential |
| Number of Predictors | 1 | 1 | 11 |
| R-squared | 0.1672 | 0.7363 | 0.8320 |
| Adjusted R-squared | 0.1645 | 0.7350 | 0.8260 |
| F-statistic p-value | 2.48E-14 | 4.75E-94 | 3.15E-112 |
| SSE | 2.86 × 10¹² | 9.06 × 10¹¹ | 5.77 × 10¹¹ |
| SD Residual | ₹94,697 | ₹53,290 | ₹42,532 |
| Mean Residual | ≈ 0 | ≈ 0 | ≈ 0 |
| Significant Variables | marketing_spend | footfall | marketing_spend, footfall, inventory_availability_decimal, customer_rating, region_South, region_West, type_Residential |
| Non-significant Variables | — | — | avg_discount_pct, region_North, type_Airport, type_HighStreet |
| Overall Model Significant? | Yes | Yes | Yes |
| Preferred Model | No | No | Yes |

* A consistent reduction in SSE across the three iterations confirms that each successive model effectively minimizes unexplained error. The Multi-Regression (MR) model demonstrates the highest predictive accuracy, yielding the lowest average residual error at ₹42,532 per store per month.

## Business Usefulness

**SR1 (marketing_spend):**
While statistically significant, this model exhibits limited explanatory power ($R^2 = 0.1672$). It serves as a baseline to validate marketing investment efficacy but lacks the depth required for autonomous sales forecasting or strategic planning. However, the identified return of ₹1.20 per ₹1 of marketing spend provides a valuable ROI benchmark for budget deliberations.

**SR2 (footfall):**
As the most robust single-variable model ($R^2 = 0.7363$), this is highly actionable for operational management. Because footfall is an observable, manageable KPI, the coefficient of ₹34.00 per visitor offers leadership a clear, data-driven target for location-based initiatives, such as loyalty programs, event planning, and visual merchandising.

**MR (all variables):**
With an $R^2$ of 0.8320, this represents the most comprehensive model for multi-faceted decision-making. It highlights that inventory management and customer satisfaction drive revenue independently of footfall. Furthermore, the model underscores the importance of store type and regional demographics, suggesting that resource allocation and sales targets should be tailored to these structural differences.

## Limitations

**SR1:**
With an $R^2$ of 0.1672, this model fails to account for 83.3% of sales variance. Its exclusion of operational and location-based variables limits its utility for standalone forecasting.

**SR2:**
Despite strong performance, this model remains incomplete, leaving 26.4% of variance unexplained. It lacks visibility into regional nuances, store-specific attributes, inventory levels, and customer sentiment.

**MR:**
Despite achieving 83.2% explanatory power, several constraints remain:
* **Model Refinement:** Four variables proved statistically insignificant, indicating a need for further optimization.
* **Linearity Assumptions:** The model assumes linear relationships that may not be consistent across diverse store profiles.
* **External Factors:** It does not currently incorporate seasonality, competitive market pressure, or macroeconomic trends.
* **Correlation vs. Causality:** These results establish association, not causal links; strategic interventions should be informed by this distinction.
