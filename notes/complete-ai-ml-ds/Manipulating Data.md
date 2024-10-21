
Remember to **practice** (the only way to learn)

How to manipulate data with `pandas`
- `car_sales('Make').str.lower()`
	- Returns a **new** `Series` whose values are the result of applying `str.lower()` to each item in the `Make` column of the `DataFrame`
	- In general, any operation one can perform on Python **strings**, one can do on "string columns" of `pandas` `DataFrames`
	- The `str` property converts the column to Python `string` values
- Changing the original column of the `DataFrame`
	- The expression, `car_sales['Make'].str.lower()`
		- **Did not** change the data in the `car_sales` `DataFrame`
		- But create a copy with the applied transformation
	- To change the original data, we must assign the changed data to the original column
		- `car_sales['Make'] = car_sales['Make'].str.lower()`
	- Some functions have a boolean parameter, typically called `inplace`. Setting `inplace=True` in the code that calculates new values will then **overwrite** the original values with the transformed values.

We often need to work with **missing data**
- For example, "car_sales_missing.csv" contains data with "holes"
	- Missing data is typical "in the wild"
- `pandas` describes missing data with `NaN` values ("not a number")
- Use `fillna()` after loading data
	- Fills `NaN` values with the **mean** of the remaining (not `NaN`) `Odometer` values
	- `car_sales_missing['Odometer'].fillna(car_sales_missing['Odometer'].mean()`
	- **BEWARE** the expression `fillna()` seems like it should **fill** the `NaN` values of `car_sales_missing['Odometer']` with the mean but it **does not**
- One could, again, assign the result of the expression back to `car_sales_missing['Odometer']`
	- However, we will actually use the `inplace=True` parameter of `fillna()`
	- This technique works **today** but will fail in `pandas` 3.x

Suppose, we:
- Are happy with filling the `NaN` values of the "Odometer" column
- But want to **ignore** all rows with `NaN` values in **any other** column
- We can accomplish this goal by running the `dropna()` method
- Again this method **does not** drop `NaN` values in place
	- But returns a **new** `DataFrame` with `NaN` values dropped
 
But what if we want to access our original data?
- Start by reading our data again