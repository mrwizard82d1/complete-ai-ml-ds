Using the dot product to calculate nut butter sales

Simulate sales amounts using our repeatable random number generator
- `sales_amounts = rng.integers(20, size=(5, 3))`
- This code generates a `numpy` array which we can put into a `pandas.DataFrame`
	- `weekly_sales = pd.DataFrame(sales_amounts, index=['Mon', ..., 'Fri'], columns=['Almond butter', ...])`

Similarly, fix our prices 
- `prices = np.array([10, 8, 12])`
- And transform these prices to a `DataFrame`
- `butter_prices = pd.DataFrame(prices, index=['Price'], columns=['Almond butter', ...]`
- Attempting to execute this statement raises a `ValueError`
	- `Shape of passed value is (3, 1), indices imply (1, 3)`
	- Remember that `prices.shape == (3,)`
		- That is, 3 **rows** by 1 **column**
	- But our `DataFrame` expects **1 row by 3 columns**
- `reshape` to the rescue!
- `butter_prices = pd.DataFrame(prices.reshape(1, 3), index=['Price'], columns=['Almond butter', ...]`

Calculating the total sales
- Using `np.dot()` appears to be a good strategy
- However, this produces a `ValueError` 
	- Because "matrices are not aligned"

We must transpose the one of the elements in our dot product
- `prices.dot(sales_amounts.T)` works!
- Apply this knowledge to our two `DataFrames`
	- `butter_prices.shape` is (1, 3)
	- `weekly_sales.shape` is (5, 3)
	- Aha! Both columns are compatible
			- But invoking `np.dot` errors because the dot product requires the same **inner dimensions**
- Try `butter_prices.dot(weekly_sales.T)`
	- `daily_sales = butter_prices.dot(weekly_sales.T)`
	- It works!
- Append that result as a new column of `weekly_sales`
	- `weekly_sales['Total ($)'] = daily_sales`
	- Oops! Another exception
		- "Exception: ValueError: Cannot set a DataFrame with multiple columns to the single column Total ($)"
	- And another row versus column error
		- `daily_sales.shape == (1, 5)`
		- But each column of `weekly_sales` has shape **(5, 1)**
- Transpose to the rescue **again**!
	- `weekly_sales['Total ($)'] = daily_sales.T`
	- Eureka!
