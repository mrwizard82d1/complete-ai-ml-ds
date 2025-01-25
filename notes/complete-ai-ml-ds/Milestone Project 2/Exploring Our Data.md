We've laid out our notebook
- And have identified the structure of our product

Load **both** training and validation sets
- Reason clarified later
```python
df = pd.read_csv('data/bluebook-for-bulldozers/TrainAndValida.csv')
```
- When I execute this line, I observe this warning (`pandas` v2.2.3 )
	- "DtypeWarning: Columns (13,39,40,41) have mixed types"
	- After a small amount of research, I will ignore this warning
	- However, consider the recommendations from https://stackoverflow.com/questions/24251219/pandas-read-csv-low-memory-and-dtype-options
- Interesting, the video encountered the same error
	- Daniel's solution: `low_memory=False`
- Reload data
```python
df = pd.read_csv(
	'data/bluebook-for-bulldozers/TrainAndValida.csv',
	low_memory=False, # Tell pandas to **not** minimize space
)
```

Peruse loaded data
```python
df.info()
```
- Notice that a number of columns have missing values
	- Because number of non-null values is **less than** the number of rows
```python
df.isna().sum()
```
- Observe many columns with > 250k missing values
```python
		df.columns
```
- Look at the columns

Let's plot some of the data
```python
fig, ax = plt.subplots()
ax.scatter(df['saledate'][:1000], df['SalePrice'][:1000])
plt.show()
```
- Plotting all the data (remove the `[:1000]` limit) produces a mostly solid color graph
- Plotting the first 1000 sales is not solid, but still not very useful

Let's try a histogram
```python
df['SalePrice'].plot.hist()
pls.show()
```
- Always a good idea to plot our target variable(s)
- In general, plotting the distribution (histogram) of a number of values useful
- Observations
	- Many values below $20k
	- Few values above $100k

The general exploratory process
- `df.info()` - Information about data frame
- `df.isna().sum()` - Identify missing values
- Scatter plot of "important columns" against target column(s)
	- In our problem, chose `saledate` column because our problem is a time series problem
- A distribution of a few columns of choice

Let's look at the `saledate` column
- Currently of dtype `object`
	- Not especially useful
	- Would like to transform to some kind of date-time object
- We will use the pandas `parse_dates` parameter
```python
df = pd.read_csv(
	'data/bluebook-for-bulldozers/TrainAndValid.csv',
	low_memory=False,
	parse_dates=['saledate'],
)
```
- The result
	- `df.saledate.dtype` prints `dtype('<M8[ns]')`

Let's plot our limited scatter plot again
```python
fig, ax = plt.subplots()
ax.scatter(df['saledate'][:1000, df['SalePrice'][:1000])
plt.show()
```
- Notice that our x-axis now has "intelligent" (and "intelligible") labels
- Look at our plot
	- A gap in sales in
		- 2005
		- 2008 (financial crisis)

We again look at our data with `df.head()`
- See columns `SalesID` and `SalePrice`
- Many different columns
- Many columns with many `NaN` (missing) values
- To understand a named column, consult our data dictionary
