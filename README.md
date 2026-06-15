# Retail Sales Analytics, Statistical Testing & Revenue Forecasting
(dataset link: https://www.kaggle.com/datasets/ahmedmohamed2003/retail-store-sales-dirty-for-data-cleaning)

## Project Overview

This project presents an end-to-end retail analytics workflow covering data validation, exploratory data analysis (EDA), statistical hypothesis testing, business intelligence reporting, and predictive revenue forecasting.

The objective was to analyze customer purchasing behavior, evaluate discount effectiveness, identify revenue drivers, understand payment preferences, uncover seasonal trends, and forecast future sales performance using machine learning.

The project combines classical Data Science techniques with business-focused decision making, moving beyond visualization into statistical validation and forecasting.

---

# Dataset

The dataset consists of retail transaction records containing:

* Transaction ID
* Product Category
* Quantity Purchased
* Price per Unit
* Total Amount Spent
* Payment Method
* Location / Sales Channel
* Discount Information
* Purchase Date

The repository contains both:

* Raw dataset
* Cleaned analytical dataset

---

# Data Quality Assessment & Cleaning

Before analysis, a comprehensive validation pipeline was executed.

## Duplicate Detection

Validated:

* Duplicate rows
* Duplicate transaction identifiers

to ensure transaction uniqueness.

## Missing Value Analysis

Performed null-value inspection across all features to verify dataset completeness.

## Revenue Consistency Validation

Verified transaction integrity using:

Total Revenue = Price per Unit × Quantity

Calculated transaction totals were compared against recorded totals to identify inconsistencies.

## Outlier Analysis

Applied the Interquartile Range (IQR) method on:

* Price per Unit
* Quantity Purchased
* Total Spend

to identify extreme observations.

## Data Type Optimization

Converted variables into suitable analytical formats:

* Boolean variables
* Categorical variables
* Date-derived temporal features

### Outcome

The dataset passed all major validation checks and was deemed suitable for downstream statistical analysis and forecasting.

---

# Exploratory Data Analysis

## 1. Category Performance Analysis

### Key Findings

| Category                         | Average Spend (₹) |
| -------------------------------- | ----------------- |
| Butchers                         | 138.6             |
| Electric Household Essentials    | 133.7             |
| Beverages                        | 132.2             |
| Computers & Electric Accessories | 129.9             |
| Furniture                        | 129.8             |
| Food                             | 128.7             |
| Patisserie                       | 128.7             |
| Milk Products                    | 119.9             |

### Discount Rates

| Category                         | Discount Rate |
| -------------------------------- | ------------- |
| Furniture                        | 69.5%         |
| Beverages                        | 68.4%         |
| Patisserie                       | 67.8%         |
| Butchers                         | 67.2%         |
| Electric Household Essentials    | 66.8%         |
| Food                             | 65.6%         |
| Milk Products                    | 65.3%         |
| Computers & Electric Accessories | 65.0%         |

### Business Insight

Higher discount rates did not consistently produce higher spending behavior, indicating that category demand characteristics were more influential than discounting frequency.

---

## 2. Revenue Seasonality Analysis

Revenue trends were analyzed across 2022–2024.

### Findings

* January consistently emerged as a peak revenue period.
* Revenue remained relatively stable throughout the year.
* December 2024 showed strong year-end performance.
* Seasonal fluctuations were observed but remained moderate.

### Business Insight

Marketing campaigns and inventory allocation should prioritize January and year-end periods where revenue demand historically peaks.

---

## 3. Discount Effectiveness Analysis

### Average Transaction Value

| Transaction Type | Average Spend |
| ---------------- | ------------- |
| Discounted       | ₹129.88       |
| Full Price       | ₹130.78       |

### Findings

* Spending distributions were nearly identical.
* Discounted purchases did not produce larger basket sizes.
* Higher discount frequency was not associated with higher spending categories.

### Business Insight

Discounts appear to create margin erosion without significantly increasing customer spending.

---

## 4. Payment Method Analysis

### Revenue by Channel and Payment Method

| Channel  | Cash     | Credit Card | Digital Wallet |
| -------- | -------- | ----------- | -------------- |
| In-Store | ₹276,770 | ₹260,450    | ₹268,239       |
| Online   | ₹290,188 | ₹273,028    | ₹268,275       |

### Findings

* Cash generated the highest revenue across both channels.
* Online Cash transactions produced the highest revenue overall.
* Digital Wallet performance remained consistent across channels.

### Business Insight

Strong Cash-on-Delivery adoption remains evident across customers, including online transactions.

---

## 5. Quarterly Revenue Analysis

### Quarterly Revenue

| Quarter | Revenue |
| ------- | ------- |
| Q1      | ₹441K   |
| Q2      | ₹400K   |
| Q3      | ₹402K   |
| Q4      | ₹394K   |

### Findings

* Q1 generated the highest revenue.
* Revenue remained relatively balanced across the remaining quarters.
* Category revenue composition remained stable throughout the year.

### Business Insight

Q1 represents the most important revenue period and should receive greater inventory and marketing investment.

---

## 6. Temporal Revenue Hotspots

A weekday-month revenue heatmap was developed to identify high-performing temporal segments.

### Findings

* Wednesday in January generated the highest observed revenue (~₹30K+).
* Monday and Friday consistently showed strong revenue performance.
* January, July, and December contained multiple revenue hotspots.

### Business Insight

Promotional activities should target historically strong weekday-month combinations.

---

# Statistical Hypothesis Testing

## H1: Do Discounts Increase Customer Spending?

### Method

Independent Two-Sample t-Test

### Results

| Metric                  | Value   |
| ----------------------- | ------- |
| Mean Spend (Discounted) | ₹129.88 |
| Mean Spend (Full Price) | ₹130.78 |
| t-statistic             | -0.5117 |
| p-value                 | 0.6089  |
| Cohen's d               | -0.0097 |

### Conclusion

No statistically significant difference was found between discounted and full-price purchases.

Effect size was negligible.

---

## H2: Are Discounts Associated With Purchase Quantity?

### Method

Chi-Square Test of Independence

### Results

| Metric               | Value  |
| -------------------- | ------ |
| Chi-Square Statistic | 2.3454 |
| Degrees of Freedom   | 2      |
| p-value              | 0.3095 |

### Conclusion

Discount allocation was statistically independent of purchase quantity.

Discounts do not appear to target larger purchases.

---

## H3: Does Payment Preference Depend on Sales Channel?

### Method

Chi-Square Test of Independence

### Results

| Metric               | Value  |
| -------------------- | ------ |
| Chi-Square Statistic | 0.5319 |
| Degrees of Freedom   | 2      |
| p-value              | 0.7665 |

### Conclusion

Payment method preference was statistically independent of sales channel.

Customer payment behavior remained consistent across Online and In-Store transactions.

---

## H4: Are Discounts Applied Differently Across Product Categories?

### Method

Chi-Square Test of Independence

### Results

| Metric               | Value   |
| -------------------- | ------- |
| Chi-Square Statistic | 12.6342 |
| Degrees of Freedom   | 7       |
| p-value              | 0.0815  |
| Cramér's V           | 0.0317  |

### Conclusion

Discount allocation was largely uniform across categories.

The effect size was negligible, indicating minimal practical association.

---

## H5: Did Revenue Change Significantly Across Years?

### Method

One-Way ANOVA

### Results

| Metric             | Value  |
| ------------------ | ------ |
| F-statistic        | 2.6360 |
| p-value            | 0.0867 |
| Eta-Squared (η²)   | 0.1378 |
| Variance Explained | 13.8%  |

### Conclusion

No statistically significant year-over-year revenue differences were detected.

However, yearly effects explained approximately 14% of total variance, indicating moderate practical influence.

---

# Revenue Forecasting

## Objective

Forecast monthly retail revenue while incorporating seasonality and historical sales patterns.

---

## Feature Engineering

The forecasting model used:

### Temporal Features

* Month Number
* January Indicator
* Q1 Indicator

### Lag Features

* Revenue (t−1)
* Revenue (t−2)
* Revenue (t−3)

### Rolling Statistics

* 3-Month Rolling Average Revenue

### Business Activity Features

* Monthly Transaction Volume

---

## Model

**Algorithm:** Linear Regression

**Training Period:** 2022–2023

**Testing Period:** 2024

**Forecast Horizon:** 6 Months

---

## Model Performance

| Metric       | Value  |
| ------------ | ------ |
| MAE          | ₹1,800 |
| RMSE         | ₹2,592 |
| MAPE         | 3.8%   |
| Test R²      | 0.256  |
| Train R²     | 0.914  |
| Residual Std | ₹849   |
| Mean Bias    | ₹613   |

### Interpretation

The model achieved low forecasting error (MAPE = 3.8%) and captured major seasonal revenue patterns.

Although test-set variance explained was modest, forecast error remained low, making the model suitable for short-term business planning.

---

## Feature Importance

| Feature            | Importance |
| ------------------ | ---------- |
| Q1 Indicator       | 2616.26    |
| Month              | 221.70     |
| Transaction Volume | 131.50     |
| January Indicator  | 65.40      |
| Lag-1 Revenue      | 0.06       |
| Rolling Average    | 0.02       |
| Lag-2 Revenue      | 0.02       |
| Lag-3 Revenue      | 0.01       |

### Key Insight

Seasonality was the strongest predictor of future revenue, with Q1 contributing significantly more predictive power than historical lag variables.

---

## Six-Month Revenue Forecast

| Month    | Forecast Revenue |
| -------- | ---------------- |
| Jan 2025 | ₹44,460          |
| Feb 2025 | ₹45,040          |
| Mar 2025 | ₹45,393          |
| Apr 2025 | ₹42,947          |
| May 2025 | ₹43,315          |
| Jun 2025 | ₹43,574          |

Confidence Interval:

± ₹1,274

---

# Business Recommendations

### Pricing Strategy

* Reduce blanket discounting policies.
* Focus discounts on categories with demonstrated sensitivity.

### Inventory Planning

* Increase stock allocation before Q1 and January demand spikes.
* Prioritize high-performing categories such as Butchers and Electric Household Essentials.

### Payment Strategy

* Continue supporting Cash-on-Delivery workflows.
* Gradually incentivize digital payment adoption.

### Marketing Optimization

* Align promotional campaigns with identified seasonal and temporal revenue hotspots.

### Revenue Forecasting

* Integrate forecasting outputs into inventory and promotional planning cycles.

---

# Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* SciPy
* Scikit-Learn
* Statistical Hypothesis Testing
* Linear Regression
* Exploratory Data Analysis
* Predictive Analytics
