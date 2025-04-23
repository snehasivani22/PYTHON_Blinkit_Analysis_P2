
# 📊 Blinkit Sales Analysis Project

This project contains a detailed analysis of Blinkit's retail data using Python. It explores patterns in sales, item characteristics, and outlet performance.

## 📁 Dataset Used

- `blinkit_data_P1.csv`  
  Contains columns like:
  - Item Type, Item Fat Content
  - Sales and Ratings
  - Outlet Establishment Year, Type, Size, Location

## 🧰 Libraries Used

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

---

## 🧹 Step 1: Data Cleaning

### Q: How is the data formatted and are there inconsistencies?

```python
df = pd.read_csv('blinkit_data_P1.csv')
df['Item_Fat_Content'].replace({'LF': 'Low Fat', 'low fat': 'Low Fat', 'reg': 'Regular'}, inplace=True)
```

- Standardized `Item_Fat_Content` values.
- Checked missing data and data types.

---

## 📊 Step 2: Exploratory Data Analysis (EDA)

### Q: What is the total and average sales?

```python
df['Sales'].sum(), df['Sales'].mean()
```

### Q: How are items distributed across fat content categories?

```python
df['Item_Fat_Content'].value_counts().plot(kind='bar')
```

### Q: Which year has the most total sales?

```python
sales_by_year = df.groupby('Outlet_Establishment_Year')['Sales'].sum().reset_index()
plt.plot(sales_by_year['Outlet_Establishment_Year'], sales_by_year['Sales'])
```

### Q: What's the contribution of each outlet size to total sales?

```python
sales_by_size = df.groupby('Outlet_Size')['Sales'].sum()
plt.pie(sales_by_size, labels=sales_by_size.index, autopct='%1.1f%%')
```

### Q: How do location types affect sales?

```python
sales_by_location = df.groupby('Outlet_Location_Type')['Sales'].sum().reset_index()
sales_by_location = sales_by_location.sort_values(by='Sales', ascending=False)
sns.barplot(x='Sales', y='Outlet_Location_Type', data=sales_by_location)
```

---

## 📌 Insights

- Sales are higher for older and larger outlets.
- Medium and High outlet sizes dominate sales.
- Urban locations consistently outperform others.

---

## 🚀 How to Run

1. Ensure you have `blinkit_data_P1.csv` and `Blinkit_P1.ipynb` in the same folder.
2. Open the notebook using Jupyter Notebook or Google Colab.
3. Run the cells step-by-step to visualize the analysis.

---

## 📎 Future Work

- Add predictive analytics (e.g., regression).
- Dashboard with Plotly or Dash.
- Customer behavior segmentation.
