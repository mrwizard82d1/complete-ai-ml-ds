We've trained the model on a subset of our data
- Our model trained quickly on our subset

How can we tune our hyperparameters?
- With `RandomizedSearchCV`
- Search for "random forest regressor hyperparameter tuning"
- We'll use `RandomizedSearchCV`

Here's our code
```python
from sklearn.model_selection import RandomizedSearchCV

rf_grid = {
	'n_estimators': np.arange(10, 100, 10),
	'max_depth': [None, 3, 5, 10],
	'min_samples_split': np.arange(2, 20, 2),
	'min_samples_leaf': np.arange(1, 20, 2),
	'max_features': [0.5, 1, 'sqrt', 'auto'],
	'max_samples': [10000],
}

rs_model = RandomizedSearchCV(
	RandomForestRegressor(
		n_jobs=1,
		random_state=rng.integers(
			np.iinfo(np.int32).max
		)
	),
	param_distribution=rf_grid,
	n_iter=6, # Video only ran 2 and took about 2 minutes
	cv=5,
	verbose=True,
)

rs_model.fit(X_train, y_train)
```

Now, find the best model hyperparameters
```python
		rs_model.best_params_
```
- My values
```python
{
	'n_estimators': 60,
	'min_samples_split': 8,
	'min_samples_leaf': 7,
	'max_samples': 10000,
	'max_features': 'sqrt',
	'max_depth': 10,
}
```

Evaluate our model with `RandomizedSearchCV` hyperparameters
```python
show_scores(rs_model)
```
- Compare to our previous scores:
```python
show_scores(model)
```
- To my both great and not so great surprise,
	- I see **no difference** between these two models

The presenter ran `RandomizedSearchCV`
- On his computer for about 2 hours
- We'll see those results in the next video
- But I wonder how different these results will be from my results?
