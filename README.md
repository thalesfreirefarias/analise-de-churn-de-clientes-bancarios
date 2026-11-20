
# 🏦 Bank Customer Churn Analysis

### Exploratory Data Analysis | Python | Pandas | Seaborn

An exploratory data analysis project focused on understanding customer churn in the banking sector.

The project investigates demographic, financial, and customer engagement characteristics associated with customer attrition.

---

## 📌 Project Overview

Customer retention is an important challenge for financial institutions.

Understanding the characteristics of customers who leave a bank can support the development of more targeted retention strategies.

This project uses Python to explore a banking churn dataset, visualize customer behavior, and identify patterns associated with attrition.

## 🎯 Objectives

- Analyze the overall customer churn rate.
- Explore demographic and financial characteristics.
- Compare churn rates across customer segments.
- Investigate relationships between engagement and churn.
- Translate analytical findings into potential business actions.

---

## 🛠️ Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Jupyter Notebook / Google Colab

---

## 📂 Repository Structure

```text
analise-de-churn-de-clientes-bancarios/
│
├── data/
│   └── Bank Customer Churn Prediction.csv
│
├── images/
│   ├── 1.png
│   ├── 2.png
│   ├── 3.png
│   └── 4.png
│
├── notebooks/
│   └── analise_de_churn_de_clientes_bancarios.ipynb
│
├── grecia.jpg
└── README.md
```

---

## 📊 Exploratory Data Analysis

### 1. Customer Churn Distribution

The dataset presents an overall churn rate of approximately **20.37%**, as reported in the analysis.

This means that roughly one in five customers in the dataset is classified as having left the bank.

**Target variable:**
- 0 = Retained customer
- 1 = Churned customer

![Customer Churn Distribution](images/1.png)

### 2. Customer Activity and Churn

Customer engagement is an important dimension of retention analysis.

The visualization compares churn behavior between active and inactive customers.

**Active Member:**
- 0 = Inactive customer
- 1 = Active customer

![Churn by Active Membership](images/2.png)

The analysis suggests an association between inactivity and customer churn.

### 3. Number of Products and Churn

This analysis explores how churn varies according to the number of banking products held by customers.

![Churn by Number of Products](images/3.png)

Differences across product segments may help identify groups requiring further investigation.

### 4. Estimated Salary and Churn

This visualization compares estimated salary distributions between retained and churned customers.

![Estimated Salary by Churn Status](images/4.png)

The objective is to explore whether salary distributions differ across churn groups.

### 5. Geographic Analysis

Churn rates were also calculated by country.

The analysis reports the following ranking:

1. Germany
2. Spain
3. France

These differences should be interpreted within the characteristics and limitations of the dataset.

---

## 🧮 Analytical Methods

The project uses:

- Data loading and inspection
- Exploratory Data Analysis (EDA)
- Grouping and aggregation
- Churn rate calculations
- Customer segmentation
- Distribution comparisons
- Data visualization

### Example: Overall Churn Rate

```python
churn_rate = df["churn"].mean()

print(f"Churn rate: {churn_rate:.2%}")
```

### Example: Churn by Customer Segment

```python
churn_by_country = (
    df.groupby("country")["churn"]
    .mean()
    .sort_values(ascending=False)
)

churn_by_activity = (
    df.groupby("active_member")["churn"]
    .mean()
)

churn_by_products = (
    df.groupby("products_number")["churn"]
    .mean()
)
```

---

## 💡 Key Findings

According to the exploratory analysis:

- The overall churn rate is approximately 20.37%.
- Inactive customers show a greater tendency to churn.
- Older customers appear more frequently among churned customers.
- Germany presents the highest churn rate among the countries analyzed.
- Churn behavior differs according to the number of banking products held.

These findings describe associations observed in the dataset and do not establish causal relationships.

---

## 💼 Business Implications

The analysis suggests potential opportunities for banking institutions to:

- Monitor customer engagement.
- Investigate segments with higher churn rates.
- Develop targeted retention initiatives.
- Evaluate customer relationships across product categories.
- Support retention decisions with data.

These are possible applications of the analysis, not validated outcomes of implemented retention strategies.

---

## ⚠️ Limitations

This project is exploratory and does not establish causal relationships.

The results depend on the dataset's characteristics, quality, and representativeness.

No predictive model performance or business impact has been validated in this analysis.

The dataset source and usage conditions should be documented before treating the results as representative of a real banking population.

---

## 👨‍💻 Author

**Thales Farias**

Financial Services | Data Analytics | Business Intelligence

📍 São Paulo, Brazil

💼 [LinkedIn](https://www.linkedin.com/in/thalesfreirefarias/)

🐙 [GitHub](https://github.com/thalesfreirefarias)

---

*Exploring banking data to transform customer behavior into actionable business insights.*
