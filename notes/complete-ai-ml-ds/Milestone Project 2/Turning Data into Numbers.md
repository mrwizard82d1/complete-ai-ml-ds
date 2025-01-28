We're making projects, but we discovered that we have data that are **not** numeric

H2 convert our non-numeric data to numeric?
- One way: converting our non-numeric data into pandas Categories

Pandas `Categorical` types
- [Categorical API](https://pandas.pydata.org/docs/reference/arrays.html#categoricals
- [Categorical data user guide](https://pandas.pydata.org/docs/user_guide/categorical.html)

Additionally, see [Pandas arrays, scalars and data types](https://pandas.pydata.org/docs/reference/arrays.html#pandas-arrays-scalars-and-data-types) 

Machine learning is about
- Getting data
- "Massaging" the data into a format amenable to a machine learning moel
- Find patterns
- Evaluating how well our steps worked

Let's investigate the `UsageBand` column
- `pd.api.types.is_string_dtype(df_tmp['UsageBand'])`
- Hmm... 
	- In the video, this function returned `True`
	- However, in my environment, this function returns `False`
	- This link summarizes the [[Changes to pandas function `is_string_dtype()`]]

After writing my own conversion function to convert 
- Columns of type `object`
- To columns of type `string`
- I then resumed the video

Now that we've  converted all our `object` columns to `string` columns, we can
- Change these `string` columns to `Categorical` columns
```python
for label, content in df_tmp.items():
	if pd.api.types.is_string_dtype(content):
		df_tmp[label] = content.astype('category').cat.as_ordered()
```
- We can "verify" the conversion by
	- `df_tmp.state.cat.codes`

But we still have missing data!
```python
df_tmp.isnull().sum() / len(df_tmp)
```
- Values of missing range from 0 to about 0.93

Let's checkpoint the preprocessed data
```python
df_tmp.to_csv('./data/bluebook-for-bulldozers/train_tmp.csv', 
			  index=False)
```

And re-import it
```python
df_tmp = pd.read_csv('./data/bluebook-for-bulldozes/train_tmp.csv',
					low_memory=False)
```

Remember that we have many **missing** values to handle
```python
df_tmp.isna().sum()
```

We'll work on missing values in the next video
