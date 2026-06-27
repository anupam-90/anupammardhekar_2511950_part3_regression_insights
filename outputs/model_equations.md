# Dummy Variable Approach & Regression Methodology

## Avoidance of Dummy Variable Trap
Including all categories within a standard regression intercept introduces perfect multicollinearity. For instance, if all four regions were included, the model would fail to isolate individual effects. By omitting one category to serve as the baseline (reference), the model can make statistically sound comparisons. If a store does not align with the three included categories, it is inherently classified as belonging to the omitted baseline.

## Explanation of Selected Reference Categories
These baselines were established for this model:

**Variable A: region**
* **Total Categories:** 4 (East, West, North, South)
* **Reference Category (Omitted):** East
* **Interpretation:** The baseline model intercept reflects the performance of a store located in the East region.

*Excel Dummy Formulas (Row 2):*
1. `reg_West`: `=IF('Cleaned Data'!C2="West", 1, 0)`
2. `reg_North`: `=IF('Cleaned Data'!C2="North", 1, 0)`
3. `reg_South`: `=IF('Cleaned Data'!C2="South", 1, 0)`

**Variable B: store_type**
* **Total Categories:** 4 (Mall, High Street, Residential, Airport)
* **Reference Category (Omitted):** Mall

*Excel Dummy Formulas (Row 2):*
1. `type_HighStreet`: `=IF('Cleaned Data'!D2="HighStreet", 1, 0)`
2. `type_Residential`: `=IF('Cleaned Data'!D2="Residential", 1, 0)`
3. `type_Airport`: `=IF('Cleaned Data'!D2="Airport", 1, 0)`

---

## Regression Models Summary

### Regression Equations
* **MODEL 1 (Sales vs. Marketing):** `monthly_sales = 560777.35 + 2.1296 * marketing_spend`
* **MODEL 2 (Sales vs. Footfall):** `monthly_sales = 446410.58 + 35.6780 * footfall`
* **MODEL 3 (Multiple Regression):** `monthly_sales = 79,339.71 + 1.2002(marketing_spend) + 34.0035(footfall) - 457.3614(avg_discount_pct) + 300,179.63(inventory_availability_pct) + 13,548.49(customer_rating) + 6,184.86(region_North) + 18,676.80(region_South) + 18,109.76(region_West) + 12,784.08(type_Airport) - 11,004.46(type_HighStreet) - 29,093.02(type_Residential)`

### 4. R-Squared
* **Model 1:** 0.1672
* **Model 2:** 0.7362
* **Model 3:** 0.8320

### 5. Coefficients (Multiple Regression)
* `marketing_spend`: 1.2002
* `footfall`: 34.0035
* `avg_discount_pct`: -457.3614
* `inventory_availability_pct`: 300,179.63
* `customer_rating`: 13,548.49
* `region_North`: 6,184.86 | `region_South`: 18,676.80 | `region_West`: 18,109.76
* `type_Airport`: 12,784.08 | `type_HighStreet`: -11,004.46 | `type_Residential`: -29,093.02

### 6. P-Values (Multiple Regression)
* `marketing_spend`: < 0.001 | `footfall`: < 0.001 | `inventory_availability_pct`: < 0.001
* `customer_rating`: 0.005 | `region_South`: 0.009 | `region_West`: 0.004 | `type_Residential`: < 0.001
* *Insignificant:* `avg_discount_pct` (0.211), `region_North` (0.380), `type_Airport` (0.187), `type_HighStreet` (0.091)

### 7. Relationship Directionality

| Variable | Direction | Significant? |
| :--- | :--- | :--- |
| marketing_spend | Positive ↑ | Yes |
| footfall | Positive ↑ | Yes |
| avg_discount_pct | Negative ↓ | No |
| inventory_availability_pct | Positive ↑ | Yes |
| customer_rating | Positive ↑ | Yes |
| region_North/South/West | Positive ↑ | Partial (South/West) |
| type_Airport/HighStreet/Residential | Mixed | Partial (Residential) |

### 8. Variable Utility Analysis
* **Marketing Spend:** Moderately useful as a baseline, but lacks sufficient explanatory power as a standalone predictor.
* **Footfall:** Highly useful. It is the dominant performance lever and remains the primary driver of sales in the full model.
* **Inventory Availability:** Highly useful. Quantifies the significant revenue impact of stockouts.
* **Customer Rating:** Useful. Provides measurable validation that service quality impacts financial outcomes.
* **Regional Effects (South/West):** Useful. Genuine regional performance differences justify differentiated target-setting.
* **Residential Type:** Useful. Flags significant structural underperformance compared to the Mall baseline.
* **Inconclusive Variables:** `avg_discount_pct`, `region_North`, `type_Airport`, and `type_HighStreet` currently lack statistical significance and are excluded from actionable strategy.

## Conclusion
**Model Selected:** Multiple Regression Model. 
**Reasoning:** With an $R^2$ of 0.8320, the Multiple Regression model explains 83.2% of the variation in monthly sales. It offers the lowest standard error and highest predictive accuracy, providing a robust, data-backed framework for strategic decision-making.
