We've create our grids for each of  models
- Let's tune them using `RandomizedSearchCV`

Let's tune our `LogisticRegression` model
```
rng = np.random.default_rng(seed=42)

rs_log_reg = RandomizedSearchCV(
	LogisticRegression(
		random_state = rng.integers(
			np.iinfo(np.int32).max
		)
	),
	param_distributions=log_reg_grid,
	cv=5, # remember, the higher the number, the longer the test
	n_iter=20,
	verbose=True,
	random_state=rng.integers(np.iinfo(np.int32).max)
)

rs_log_reg.fit(X_train, y_train)
```
- And then view our best parameters
```python
rs_log_reg.best_params_
```
- And score the model using these parameters
```python
rs_log_reg.score(X_test, y_test)
```
- The video reports the same (or similar) score
- In my experiment, the result is slightly worse

| Previous | Tuned  |
| -------- | ------ |
| 0.8033   | 0.7869 |

We've tuned `LogisticRegression`; now let's tune `RandomForestClassifier`
```python
rng = np.random.default_rng(seed=42)

rs_rf = RandomSearchCV(
	RandomForestClassifier(
		random_state=rng.integers(np.iinfo(np.int32).max)
	),
	param_distributions=rf_grid,
	cv=5,
	n_iter=20,
	verbose=True,
	random_state=rng.integers(np.iinfo(np.int32).max)
)

rs_rf.fit(X_train, y_train)
```
```python
rs_rf.best_params_
```
```python
rs_rf.score(X_test, y_test)
```
- Comparing our results

| Previous | Tuned  |
| -------- | ------ |
| 0.7541   | 0.8688 |

What are our results
- Our `RandomForestClassifier` results improved
	- In the video, not yet as good as `LogisticRegression`
	- In my notebook, better than `LogisticRegression`

Now that we've randomly searched the hyperparameter space
- We may want an **exhaustive search** to truly narrow our results

Three ways to tune our model:
1. By hand
2. `RandomizedSearchCV`
3. `GridSearchCV`

In the video, the plan is to
- Use `GridSearchCV` for the `LogisticRegression` model
- I may try to use `GridSearchCV` for the `RandomForestClassifier` model

