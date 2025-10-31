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

### 2. Money Patterns (money_patterns.ipynb)

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

### 3. Model Building for Price Prediction (models.ipynb)

After finishing the analysis, I started working on predictive modeling.

At first, I have built a linear model, that worked quite well. The results were:
R²: 0.8700882669455114
RMSE: 1.7239347220842336

The model was not overfitting much, after checking cross_val_score, it turned out to be:
Average CV R²: 0.7783000777729638

However, I wanted to go further to improve model performance. I tried RandomForestRegressor, and it was significantly outperforming (**R² ≈ 0.99 and RMSE ≈ 0.51**) the linear model (**R² = 0.87, RMSE ≈ 1.72**). This indicates that the relationship between coffee type, time features, and sales is nonlinear and interaction-based. Random Forest captures these dependencies effectively, leading to near-perfect prediction accuracy on held-out data.

This seemed like a win, but this model was overfitting. I tried to create 5 cross validation scores, and the outcome was not great:

Cross-validation R²: [0.81419226 0.72478313 0.74161085 0.99912936 0.82551351]
Mean: 0.8210458223661291 Std: 0.09732121986961685

I tried 4 different potential solutions: 
- Limiting Depth 
- Using fewer Features
- Using fewer Trees
- Increasing Minimum Samples per Split / Leaf

Using fewer trees proved to be the best solution. To visualize the progress, I compared cv scores to train R² on different max_depths for initial RandomForestRegressor and for better one. I also took double the amount of cvs, so the progress would be visible.
Initial:
![alt text](initial_rfr.png)
Improved:
![alt text](optimized_rfr.png)

### Final Thoughts

I couldn't create a fully realistic model, using the dataset. This might be connected with me not being knowledgeable enough. This also might be connected with limited variance of money spent. There are some amounts, that pop up unrealistically often, as seen in the analysis part of the project. 

However, it is true that in real world bestsellers can create such outlying amounts. Hence, how can overfitting be avoided in this situations?