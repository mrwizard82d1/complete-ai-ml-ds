
A few more functions to introduce

Functions
- `samples()` - shuffles the data (depending on `frac` argument value)
	- Returns a new instance consisting of `frac * len(source)` rows 
	- However, the index of the returned rows has been randomly shuffled
		- For example,

| Current Row | Original row index |
| ----------- | ------------------ |
|             | 5                  |
| 1           | 3                  |
| 2           | 7                  |
| And...      | ...so on           |
	- We may want to **practice** on a small amount of randomly sampled data
		- For example, `car_sales_shuffled.sample(frac=0.2)` which randomly selects 20% of the (shuffled) data
- `reset_index()` - used to "unshuffle" the index
	- The behavior of `reset_index()` has apparently changed since the video was produced 
	- No longer retains a column named `index`
	- Review documentation for `pandas.reset_index()`

Apply a function to a `DataFrame`
- Suppose we want to convert km to mi
- Use `apply()` with a `lambda` expression
	- `car_sales['Odometer (mi)'] = car_sales['Odometer (KM)'].apply(lambda x: x / 1.6)`

Remember that much of data science is about **learning**
- Try it
- Run your code
- If in doubt, search for a solution
- Try again
- If still stuck, **ask**

