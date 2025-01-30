Now that we only have numeric values and no missing values
- We can again fit a regression model

We want to
- Drop the 'SalePrice' column
- Create a machine learning (regression) model using the remaining columns to 
	- Predict 'SalePrice'

We'll calculate the time it takes to run our regression
- Using the Jupyter notebook `%%time` "magic function"
```python
%%time
model = RandomForestRegression(
	n_jobs=1,
	random_state=rng.integers(np.iinfo(np.int32).max),
)
model.fit(df_tmp.drop('SalePrice', axis=1), df_tmp['SalePrice'])
```
- Execution took 1:05 min on my M1 Mac
- Execution took 6:58 min on presenter's Mac

Let's score our model
```python
model.score(df_tmp.drop('SalePrice', axis=1), df_tmp['SalePrice']))
```
- We scored 0.9876
- Seems great but...
- We scored the model on the same data on which we trained it
	- The real question then might be
		- "Why not a perfect score (1.0)?"

We'll talk about this in the next video
