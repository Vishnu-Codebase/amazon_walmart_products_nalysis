# 📊 Amazon vs Walmart Product Data Analysis

## 📌 Project Overview
This project analyzes and compares product data from Amazon and Walmart to understand pricing patterns, customer ratings, and discount behavior. The goal is to extract meaningful business insights using data cleaning, exploratory data analysis (EDA), and visualization techniques.

---

## 🎯 Project Objectives
- Compare product prices across Amazon and Walmart
- Analyze customer rating patterns
- Study discount trends
- Identify outliers and anomalies
- Generate actionable business insights

---

## 📂 Dataset Description
The dataset contains product information collected from Amazon and Walmart.

| Column Name     | Description                         |
|-----------------|-------------------------------------|
| platform        | Source platform (Amazon/Walmart)    |
| final_price     | Product selling price               |
| initial_price   | Original price                      |
| discount        | Discount amount                     |
| rating          | Customer rating (1–5 scale)          |
| brand           | Product brand name                  |
| categories      | Product category                    |
| currency        | Currency type                       |
| description     | Product description                 |

---

## 🧹 Data Cleaning & Preprocessing
The following preprocessing steps were performed:

- Removed unnecessary columns (`ingredients`, `upc`, `url`)
- Converted price and discount columns to numeric format
- Removed `$` symbols from currency values
- Handled missing ratings by replacing `0` with `1`
- Filled missing brand values with `"Unknown"`
- Identified outliers using the IQR method
- Resolved chained assignment warnings
- Standardized data formats

---

## 📊 Exploratory Data Analysis (EDA)

### Univariate Analysis
- Distribution of product ratings
- Distribution of prices
- Discount frequency analysis

### Bivariate Analysis
- Platform vs Price
- Platform vs Rating
- Rating vs Discount

### Multivariate Analysis
- Pivot tables
- Correlation analysis
- Platform–Category–Price relationships

---

## 📈 Visualizations
Visualizations were created using Matplotlib and Seaborn:

- Histograms
- Box plots
- Scatter plots
- Bar charts
- Heatmaps

All charts include proper titles, labels, and legends.

---

## 🔍 Key Insights
- Amazon products are priced higher on average than Walmart products.
- Walmart products receive better customer ratings.
- Most products have little or no discount.
- Initial price and final price are strongly correlated.
- Ratings show weak correlation with pricing.
- Extreme price outliers influence average values.

---

## ⚠️ Limitations
- Many ratings were missing and replaced with minimum values.
- Category and currency columns contain noisy and unstructured data.
- Presence of extreme outliers.
- Some duplicate and inconsistent records.

---

## ⚙️ Installation Guide

Follow the steps below to run this project locally.

### 1️⃣ Prerequisites
Ensure the following are installed:

- Python 3.8 or above
- Jupyter Notebook
- pip

Check versions:

```bash
python --version
pip --version
```
```bash
git clone 'https://github.com/Vishnu-beep-hub/amazon-walmart-product-analysis.git'
```

Please look at the requirements.txt to install packages using pip
```bash
pip install -r requirements.txt
```


👨‍💻 Author

Vishnuraj M

Data Analyst | Full Stack Developer | Machine Learning

- 🌐 Portfolio: https://portfolio-reactjs-tensor-flow-wiy9.vercel.app
- 💼 LinkedIn: https://linkedin.com/in/vishnurajagopalan-pixel
- 📧 Email: vishnurajagopalanmannilvr@gmail.com
- 🐙 GitHub: https://github.com/Vishnu-beep-hub
