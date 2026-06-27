# FINAL RECOMMENDATION 

## Business Interpretation of each Regression Model

### Monthly_sales vs Marketing Spend
There is a positive, statistically significant relationship between marketing spend and monthly sales. On average, every ₹1 invested in marketing returns approximately ₹2.13 in sales, indicating a positive ROI. However, an $R^2$ of 0.1672 suggests that marketing spend alone leaves 83.3% of sales variation unexplained. While this model is insufficient for standalone sales forecasting, it confirms that marketing investment is yielding measurable returns.

### Monthly_sales vs Footfall
Footfall is the strongest single predictor of monthly sales in the dataset. A ₹35.68 sales increase per additional visitor indicates that strategies to drive store traffic—such as loyalty programs, promotional events, and improved visibility—have a direct and substantial revenue impact. The high $R^2$ of 0.7363 demonstrates that this variable captures nearly three-quarters of sales variance, making it an essential KPI for management to monitor and prioritize.

### Multiple Regression Model
* **Marketing_spend (₹1.20):** Every additional ₹1 of marketing spend is associated with ₹1.20 in monthly sales, holding other factors constant. The decrease from the simple regression coefficient (₹2.13) indicates that footfall and other variables are now accounting for variance previously attributed solely to marketing.
* **Footfall (₹34.00):** Each additional visitor adds ₹34.00 to monthly sales, consistent with our simple regression findings. Footfall remains the most impactful numerical predictor even when controlled for 10 other variables.
* **Inventory_availability_pct (₹30,018 per 10% improvement):** Moving from 80% to 90% availability is associated with approximately ₹30,018 in additional monthly sales, highlighting the high cost of stockouts.
* **Customer_rating (₹13,548):** Each one-point improvement in customer rating is associated with ₹13,548 more in monthly sales, confirming that service quality delivers a tangible financial return.
* **Region_South (₹18,677) and Region_West (₹18,110):** After controlling for all other variables, South and West stores outperform the East region baseline by these amounts, respectively.
* **Type_Residential (−₹29,093):** Residential stores significantly underperform Mall stores (the baseline). This structural gap likely reflects lower footfall and reduced impulse purchasing behavior.

---

## Variables That Are Statistically Weak or Difficult to Interpret

* **avg_discount_pct:** Not statistically significant. The negative coefficient likely reflects "reverse causality," where struggling stores discount more heavily to recover sales. This variable should be excluded from future models.
* **region_North:** Not statistically significant. No reliable evidence exists to suggest North stores perform differently than the East baseline.
* **type_Airport:** Not statistically significant ($p = 0.187$). While directionally positive, the result is too unreliable to inform strategy.
* **type_HighStreet:** Not statistically significant ($p = 0.091$). While the negative coefficient aligns with broader retail trends, it does not meet the 0.05 threshold and should be excluded from refined models.

---

## Is This Variable Useful?

### Simple Regression Models
* **Marketing Spend:** Moderately useful as a baseline, but lacks the explanatory power to be a standalone predictor.
* **Footfall:** Highly useful. It remains the dominant performance lever in both simple and multiple regression models.

### Multiple Regression Model
* **Marketing Spend:** Useful. Maintains a significant positive return of ₹1.20 per ₹1 invested.
* **Footfall:** Highly useful. It is the primary driver of revenue and should be the focal point of performance strategies.
* **Inventory Availability:** Highly useful. Quantifies the direct revenue impact of supply chain reliability.
* **Customer Rating:** Useful. Demonstrates that customer experience is a measurable revenue driver.
* **Region_South & West:** Useful. Confirms genuine regional performance advantages.
* **Type_Residential:** Useful. Acts as a critical flag for structural performance gaps that require differentiated targets.

---

## Final Business Recommendations

### 1. Factors Most Strongly Associated with Monthly Sales
Footfall is the dominant driver of sales. Inventory availability, customer rating, marketing spend, and regional location are also statistically significant. Collectively, these factors explain 83.2% of sales variance. Residential store type represents a significant structural performance challenge.

### 2. Variables Leadership Should Focus On
* **Footfall:** The highest priority KPI for store performance.
* **Inventory Availability:** A measurable operational lever; reducing stockouts directly boosts revenue.
* **Customer Rating:** Should be treated as a core revenue metric rather than a "soft" operational indicator.
* **Marketing Spend:** Maintain current investment levels, as it provides a stable ROI.

### 3. Variables That Should Not Be Over-interpreted
Variables such as `avg_discount_pct`, `region_North`, `type_Airport`, and `type_HighStreet` lack statistical significance. Leadership should avoid basing operational changes on these metrics until further data or more rigorous controls are implemented.

### 4. Recommended Business Actions
1.  **Drive Footfall:** Invest in loyalty schemes, promotional events, and location visibility.
2.  **Differentiate Targets:** Adjust sales expectations for Residential stores to reflect their structural performance gap.
3.  **Optimize Inventory:** Prioritize supply chain improvements to minimize stockouts.
4.  **Formalize Service Standards:** Integrate customer rating KPIs into store management performance reviews.
5.  **Regional Benchmarking:** Analyze South and West operations to replicate best practices in the East and North regions.

### 5. Risks and Limitations
* **Seasonality:** The dataset only covers four months (Jan–April 2025); results may change over a full annual cycle.
* **Unexplained Variance:** 16.8% of variance remains unaccounted for, potentially due to competitor activity or macroeconomic shifts.
* **Model Reliability:** Residual analysis indicates the model is less accurate for High Street and West region segments.

### 6. Why Regression Shows Association and Not Causation
A significant coefficient indicates correlation, not a guaranteed outcome of intervention. For instance, the negative impact of discounts likely reflects reactive discounting by underperforming stores. These findings are best used to prioritize areas for controlled testing and further investigation rather than as proof of guaranteed sales uplift.
