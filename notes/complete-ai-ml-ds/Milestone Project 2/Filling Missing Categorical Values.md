We've filled our numerical missing values
- Let's repeat this exercise for other types
- Primarily `Categorical` but may be others

Here's our code to find columns with null values that are not of type numeric
```python
for label, content in df_tmp.items():
	if not pd.api.types.is_numeric_dtype(content):
		if pd.isnull(content).sum()
			print(label)
```

Let's look at a typical column of type `Categorical`: 'state'
```python
pd.Categorical(df_tmp.state)
```
- We can also query the `dtype`
	- `pd.Categorical(df_tmp.state).dtype`
- And the `codes`
	- `pd.Categorical(df_tmp.stage).codes`
		- The values in the returned `np.array` are of type `int8`!
		- The `codes` property is how we can turn `Categorical` values into numbers

How do we turn our `Categorical` columns into numbers?
```python
for label, content in df_tmp.items():
	if not pd.api.types.is_numeric_dtype(content):
		# Add a binary column to "remember" our missing values
		df_tmp[label + '_is_missing'] = pd.isnull(content)
		# Turn categories into numbers **but add 1**
		# We add 1 because the `Categorical` `dtype` encodes all 
		# missing/null/None values as the integer, -1. Adding 1
		# ensures that all our Categorical columns have 
		# **non-negative** values.
		df_tmp[label] = pd.Categorical(content).codes + 1
```

Let's ensure we have no more missing values
```python
np.any(df_tmp.isna().sum != 0)
```
- This expression returns `False`

We now know that all our data
- Is **numeric**
- Has no missing values

What is the significance of this state?
- We'll find out in the next video
