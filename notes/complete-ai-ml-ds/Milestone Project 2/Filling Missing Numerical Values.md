Remember [this link]([https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.Categorical.html](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.Categorical.html)) to documentation of the pandas `Categorical` type 

We ended our previous work "discovering" that we had missing values

Let's fill our missing values - numeric missing values first
- Identify numeric columns
```python
for label, content in df_tmp.items():
	if pd.api.types.is_numeric_dtype(content):
		print(label)
```
- Just for grins if using `cytools.curried as ctc`
```python
ctc.pipe(
	df_tmp.items(),
	ctc.filter(lambda t: pd.api.types.is_numeric_dtype(t[1])),
	ctc.map(ctc.first)
	list,
)
```

Find which numeric columns have null values
```python
for label, content in df_tmp.items():
	if pd.api.types.is_numeric_dtype(content):
		if pd.isnull(content).sum():
			print(label)
```
- Or
```python
ctc.pipe(
	df_tmp.items(),
	ctc.filter(lambda t: pd.api.types.is_numeric_dtypes(t[1])),
	ctc.filter(lambda cn: pd.isnull(cn).sum()),
	ctc.map(ctc.first),
	list,
)
```

Fill the null values in the (two) numeric columns with the median of the column values
```python
for label, content in df_tmp.items():
	if pd.api.types.is_numeric_dtype(content):
		if pd.isnull(content).sum():
			df_tmp[label + '_is_missing'] = pd.isnull(content)
			df_tmp[label] = content.fillna(content.median())
```

Why use the median and not the mean?
- The median is **more robust** in the presence of outliers
- That is, the median changes less than the mean in the presence of outliers

Check again for null values in any numeric columns
- Repeating the previous code **prints nothing**

Does our "is missing" column remember all the missing values?
```python
df_tmp['auctioneerID_is_missing'].value_counts()
```
- The result of this expression is a `DataFrame` indicating 20,136 missing value
- The same as previously in our notebook

We've now filled all the numeric values, but we must fill the other columns that have missing values
```python
df_tmp.isna().sum
```

We'll work on other (`Categorical`) missing values in the next video
