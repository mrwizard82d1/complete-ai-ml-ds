Look at different ways to describe data

All available completions
- In notebook (without vim enabled)
	- Enter text (ending with a dot ('.'))
	- The press Tab
- In `jupyter lab` with `vim`
	- ESC to enter command mode
	- Move beyond terminating period ('.')
	- Press TAB

Remember that describing and running functions over a `DataFrame` most often occurs when **exploring** the data

Describing data using **attributes**
- `dtypes`
	- Information about column of the data frame
		- Name of the column
		- Type of data in that column
- `columns`
	- Returns a `pd.Series` (`Index`) describing the column names
- `index`
	- A description of the index of a `Series`

Invoking data **functions**
- `describe()`
	- Provides statistical information about (some) of our `DataFrame` **columns**
		- `count`
		- `mean`
		- `std`
		- `min`
		- `25%`
		- `50%`
		- `75%`
		- `max`
	- Only provides statistics for **numeric** columns
		- Notice that `price` is **not** numeric but has type `object`
- `info()`
	- Provides information about each column of a `DataFrame`
	- Like a combination of `index` and `dtypes`
- `mean()`
	- Calculates the arithmetic mean of each column
	- Previous behavior:
		- Skipped non-numeric values
	- Current behavior
		- **Includes** non-numeric values
		- Which produces **errors**
	- To restore previous behavior, evaluate the function:
		- `car_sales.mean(numeric_only=True)`
- `sum()`
	- Notice that object columns are **concatenated**; that is, invokes `str.sum()` (I think)
	- May be more useful to call on a single column
		- For example, `car_sales['Odometer (KM)'].sum()`
- `len(car_sales)` 
	- Length of the data frame

