# Retail Chain Sales Performance Regression Analysis

## Task 1: Dataset Review and Variable Identification

Based on the provided dataset and data dictionary, the regression analysis framework is defined as follows:

### 1. Dependent Variable
* **`monthly_sales`**: This is the outcome variable we aim to explain and predict.

### 2. Potential Independent Variables
* `marketing_spend`, `footfall`, `avg_discount_pct`, `staff_count`, `inventory_availability_pct`, `competitor_distance_km`, `holiday_flag`, `customer_rating`, `region`, `store_type`.

### 3. Numerical Variables
* `marketing_spend`, `footfall`, `avg_discount_pct`, `staff_count`, `inventory_availability_pct`, `competitor_distance_km`, `customer_rating`, `monthly_sales`, `monthly_profit`.

### 4. Categorical Variables
* `region`, `store_type`, `holiday_flag` (binary/categorical).

### 5. Variables Requiring Cleaning or Transformation
* **`month`**: Needs to be converted to a datetime object or extracted to seasonal features.
* **Categorical Encoding**: `region` and `store_type` require One-Hot Encoding or Label Encoding to be used in a regression model.
* **`holiday_flag`**: Already binary, but ensure consistency.

### 6. Variables that may not be useful for regression
* **`store_id`**: An identifier, not predictive of performance.
* **`monthly_profit`**: Highly correlated with `monthly_sales` and essentially a result of sales; using it as an independent variable would cause multicollinearity and leak the outcome.
