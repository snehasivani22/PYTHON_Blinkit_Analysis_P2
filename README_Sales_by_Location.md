
# Sales Analysis by Outlet Location Type

This script analyzes and visualizes the total sales by different outlet location types using Python's pandas, matplotlib, and seaborn libraries.

## Code Explanation

```python
sales_by_location = df.groupby('Outlet_Location_Type')['Sales'].sum().reset_index()
```
- Groups the dataset by `Outlet_Location_Type`.
- Aggregates the sales data by summing it up for each location type.
- Resets the index for clean dataframe handling.

```python
sales_by_location = sales_by_location.sort_values('Sales', ascending=False)
```
- Sorts the grouped data in descending order based on total sales.

```python
plt.figure(figsize=(8, 3))
```
- Sets the figure size to 8 inches wide and 3 inches tall.

```python
ax = sns.barplot(x='Sales', y='Outlet_Location_Type', data=sales_by_location)
```
- Uses seaborn's barplot to create a horizontal bar chart.
- `x='Sales'` plots sales on the X-axis.
- `y='Outlet_Location_Type'` uses outlet location type on the Y-axis.
- `data=sales_by_location` provides the processed dataset.

```python
plt.title("Total Sales by Outlet Location Type")
plt.xlabel("Total Sales")
plt.ylabel("Outlet Location Type")
```
- Adds a title and labels to the plot for clarity.

```python
plt.tight_layout()
plt.show()
```
- Adjusts the layout to prevent clipping of labels.
- Displays the plot.

## Requirements

- pandas
- matplotlib
- seaborn

Make sure to install the required packages before running this script:
```bash
pip install pandas matplotlib seaborn
```
