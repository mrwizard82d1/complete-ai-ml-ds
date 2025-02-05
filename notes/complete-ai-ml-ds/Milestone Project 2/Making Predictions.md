We now have a function to preprocess our data
- Let's now run our data through our function
- And then test it

Let's run `preprocess_dataset()`
- Result: 101 columns
- Not quite the same.

Again, running `predict()` throws an exception
- We can see the missing column by
```python
set(X_train.columns) - set(df_test.column)
```
- Results in {'auctioneerID_is_missing'}

One way to address this is to 
- Add a column named `auctioneerID_is_missing`
	- The reason
		- In our test data, `auctioneerID` has **no** missing values
```python
# Evaluates to `True`
df_test['auctioneedID'].isna().sum() == 0 
```
- Therefore, let's create our missing column and hard-code all values to `False`
- `df_test['auctioneedID_is_missing] = False`
- And now `df_test` has the same columns as X_train
	- `set(X_train.columns) - set(df_test.columns)`
		- Returns an empty set

However, when I execute this code, I **still** see the exception
- I tried the function `pd.DataFrame.align()`
```python
_, df_tmp = df_test.align(X_train, join='outer', axis=1)
```
- The operation does not work
- Both `df_tmp` and `X_train` have the some columns, but **in a different order**
	- `set(X_train.columns) - set(df_tmp.columns)` returns an empty set
	- `list(X_train.columns) == list(df_tmp.columns)` returns `False`

Let me try inserting the `auctioneerID_is_missing` column in the correct location
- After much experimentation, discovered the pandas function `DataFrame.reindex`
```python
df_test = df_test.reindex(columns=X_train.columns)
```
- `set(X_train.columns) - set(df_test.columns)` returns `set()`
- `list(X_train.columns) == list(df_test.columns)` returns `True`
- Finally!

We've made some predictions but they are **not** in the format required by Kaggle
- www.kaggle.com/competitions/bluebook-for-bulldozers/overview/evaluation
- Here's a simple way to format them
```python
df_preds = pd.DataFrame()
df_preds['SalesID'] = df_test['SalesID']
df_preds['SalePrice] = test_preds
```

Our data is now in the right format. Time to export:
```python
df_preds.to_csv(
	'data/bluebook-for-bulldozers/my_test_predictions.csv', 
	index=False
)
```

We've used the patterns found by our model
- We might examine feature importance next
	- That is, which features have the most impart on our predictions
- In the next video
