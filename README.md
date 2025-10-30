## Coffee Project

This small data analysis project explores patterns in coffee sales data. The goal was to uncover insights about trends and purchases' patterns using Python data analysis tools and visualizations. The dataset was taken from Kaggle: https://www.kaggle.com/datasets/sidraaazam/coffee-sales-insights-report

### Project Structure

Coffe_sales.csv: Source dataset with sales and transaction details

date_analysis.ipynb: Focuses on time-based analysis and visualization

money_patterns.ipynb: Focuses on financial data transformation and normalization

### 1. Date Analysis (date_analysis.ipynb)

**Objective:**
Understand how sales vary across different days of the month.

**Process:**

- Parsed the Date column using pandas.to_datetime.

- Extracted the day of the month (.dt.day).

- Counted frequency of transactions per day.

![alt text](freq_days_graph.png)

*Observation:* 31st appears less frequently since not all months have it. It is clear that coffee is an everyday habit, given the transactions in the dataset.

💰 2. Money Patterns (money_patterns.ipynb)

**Objective:**
Explore and preprocess monetary data for better statistical analysis.

**Process:**

- Checked for missing values (none found).

- Scaled money column using Min–Max scaling.

- Applied Box–Cox normalization to reduce skewness.

- Compared distributions before and after transformations.

**Visualizations:**

Histogram — Original vs Scaled Data

![alt text](orig_n_scaled_graph.png)

Histogram — Original vs Normalized (Box–Cox) Data

![alt text](orig_n_scaled_graph.png)

Insight: Scaling preserves distribution shape; Box–Cox normalization improves normality, preparing data for advanced modeling.

**Tools and Libraries**

*Python:* pandas, numpy, matplotlib, seaborn, scipy, mlxtend


**Summary**

Data cleaning and feature engineering completed for both temporal and monetary dimensions. Clear workflow demonstrates end-to-end preprocessing and exploratory data analysis (EDA).

Visual analyses confirm consistent patterns and transformations ready for modeling. This project, for now, is a simple EDA, that I want to turn into a compelling *predictive modeling project*
