We've copied our original data into `df_tmp`
- Now we'll use the `saledate` to **enrich** our data frame

What is _feature engineering_?
- Adding new "columns" to our data frame
- How can we do this with our `saledate`?

The `pandas` package provides tools to query a time point **in detail**
- For example,
	- `nanosecond`
	- `is_month_end`
	- `is_quarter_start`
	- `is_year_end`

Let's calculate the year of the sale
```python
# Begin by some queries to understand the 
# `datetime` attributes and methods
df_tmp[:1].saledate.dt.year
df_tmp[:1].saledate.dt.day

# Enrich our dataframe 
df_tmp['saleyear'] = df_tmp['saledate'].dt.year
df_tmp['salemonth'] = df_tmp['saledate'].dt.month
df_tmp['saleday'] = df_tmp['saledate'].dt.day
df_tmp['saledayofweek'] = df_tmp.saledate.dt.dayofweek
df_tmp['saledayofyear'] = df_tmp.saledate.dt.dayofyear

# Look at the end of our columns to see the new columns
df_tmp.head().T.taila
```
- And now let's remove the original `saledate` column
```python
df_tmp.drop('saledate', axis=1, inplace=True)
'saledate' in df_tmp.columns
```
- `saledate` no longer in `df_tmp` but **still in `df`**

Let's do a little more exploring?
- Which state has the most sales?
- `df_tmp.state.value_counts()`

We've done some EDA (exploratory data analysis); let's do some modeling!
- More specifically let's perform _model-driven EDA_
- What is _model-driven EDA_?
	- Our original data frame has **many, many** features
	- Since we already know our goal
		- Use all the independent variables to predict `SalePrice`
- What kind of learning should we do?

Back to our [Online machine learning model map](https://scikit-learn.org/stable/machine_learning_map.html)
- Start
- > 50 samples - True
- predicting a **category** - False
- predicting a **quantity** - True
- < 100k samples - True
- Because we've had some experience with `RandomForestClassifier`
	- Let's check out its regression counterpart, `RandomForestRegressor`

Let's build a machine learning model
```python
from sklearn.ensemble import RandomForestRegressor

model = RandomForestRegressor(
	n_jobs=1, # Use all available processors
	random_seed=rng.integers
)

try:
	model.fit(df_tmp.drop('SalePrice', axis=1), df_tmp['SalePrice'])
except ValueError as ve:
	print(ve)
```
- This code prints an error message!
	- "could not convert string to float"
- Let's look at our columns
	- `df.info()`
	- The output of this command reminds us that many of our columns
		- **Are not numbers**

Let's look at some of our `object` types?
- `df_tmp['UsageBand'].head()`

We have a (modeling) problem
- We have a bunch of data that is
	- Non-numeric
	- Missing
- We need to address our **data** before we can perform exploratory data analysis (EDA)
