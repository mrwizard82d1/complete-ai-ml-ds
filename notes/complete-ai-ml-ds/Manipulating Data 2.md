
Adding a column to a `DataFrame` by assignment
- Create a `Series` with some data
- Assign the newly created `Series` to a column of the `DataFrame` with a non-existent name
	- The `DataFrame` `car_sales` exists
	- The `Series` `seats_column` exists
	- Before the assignment, `car_sales["Seats"]` **does not exist**
		- The assignment brings the new column "into existence"
- Can then use `fillna()` to fill in `NaN` values with same value (5)
	- **NOTICE**
		- Since the original value was floating point
			- Calling `fillna(5)` will coerce all values to integral values (**with a warning**)
			- To avoid warning, call `fillna(5.0)`

One can also create a column by assigning a Python list
- However, the Python list
	- **Must** have the same length as the target `DataFrame`; that is, one must supply a value for **each row**

One can create one column from another column
- For example, suppose one wanted to calculate the total fuel used over its lifetime (so far)
	- `car_sales['Total Fuel Used (L)'] = (car_sales['Odometer (KM)'] / 100) * car_sales['Fuel per 100KM']`

Create a column from a single value
- Behavior relies on "broadcasting"
- Two examples
	- `car_sales['Number of Wheels'] = 4`
	- `car_sales['Passed Road Safety'] = True`

How would I remove a column?
- `car_sales = car_sales.drop('Total Fuel Used', axis = 1)`

