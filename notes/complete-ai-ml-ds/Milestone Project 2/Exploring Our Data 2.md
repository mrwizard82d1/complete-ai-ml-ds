Our data is now in a good, but not final, format

Our data has many columns
- Here is a "trick" to view these many columns
- Transpose the head (or tail) of the data frame
	-  `df.head().T`

Because we have many columns, trying to look at them all will
- **Take much time**
- How can we address this issue?
- Let's look at our sale dates
	- `df.saledate.head()`
	- What conclusion(s) can we draw
		- We are interested in sales price by date, but "raw" data
			- **Not** ordered by `saledate`

To look at time ordered data, let's sort it
- Generally, when looking at time series data, sort it by the "time" column
	- By `saledate`
- `df.sort_values(by=['saledate'], inplace=True, ascending=True)`
	- Remember that sorting timewise results from our previous 
		- Parsing into datetime object

A good idea to make a **copy** of the original data frame
- Allows us to repeat calculations if we have made a mistake
- That is, we have created a **check point**
