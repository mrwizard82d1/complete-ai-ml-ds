ast video, saw h2 tune hyperparameters using `RandomizedSearchCV`
- Now we'll search exhaustively using `GridSearchCV`

An workflow to tuning hyperparameters
1. Begin by tuning parameters by-hand
2. Then use random search using `RandomizedSearchCV` across a space of parameters
3. Once you've found good hyperparametirs, use `GridSearchCV` to search exhaustively

We already have a grid of parameters
- `RandomizedSearchCV` has an `n_iter` parameter
	- **Limits** the number of parameters to consider
- `GridSearchCV` performs an **exhaustive** search
	- In our example, we have a search space of
		- 6x5x2x3x3x5 = 2700

Let's create a "reduced" grid for our search
- One option
	- Copy and paste `grid` to `grid_2`
- A suggested option
	- Use the result of `RandomizeSearchCV` to prune `grid` into `grid_2`
	- That is, use `classifier.best_params_` to influence how we "prune" the `grid_2` values initialized from the values of `grid`

Our tentative search space:
```python
grid_2 = {
	`n_parameters`: [200, 500, 2000],
	'max_depth': [30],
	'max_features': ['sqrt', 'log2'],
	'max_samples_split': [6],
	'max_samples_leaf': [1, 2],
}
```
- Search of 60 parameters 
	- Instead of 2700

Our search code:
```python
from sklearn.model_selection import (
	 GridSearchCV,
	 train_test_split,
)

rng = np.random.default_nrg(seed=42)

X = heart_disease_shuffled.drop(
	'target',
	axis=1,
)
y = heart_disease_shuffeld['target']

X_train, X_test, y_train, y_test = \
	X, y, test_size=0.2,
	random_state=rng.integers(
		np.iinfo(np.uint32).max
	)

classifier = RandomForestClassifier(
	random_state=rng.integers(
		np.iinfo(np.unit32).max
	),
	n_jobs=1,
)

gs_classifier = GridSearchCV(
	 estimatar=classifier,
	 param_grid=grid_2,
	 cv=5,
	 verbose=2
)

gs_classifier.fit(X_train, y_train)
```

Again, when finished, query
- `gs_classifier.best_params_`

Remember,
- `GridSearchCV` may take some time to finish

The result: slightly different parameters
```python
{'max_depth': 20,
 'max_features': 'sqrt',
 'min_samples_leaf': 2,
 'min_samples_split': 6,
 'n_estimators': 500}
```

Time to test our predictions:
```python
gs_y_predictions = \
	gl_classifier.predict(X_test)

gs_metrics = evaluate_predictions(
	y_test, gs_y_predictions
)
```

in general, not much improvement
- Points out that tuning is a 
	- **Process**
	- Not **a formula**

Hyperparameter tuning
- Is **not** a science
- All about trial and error
- Suggested work flow
	- Try a few hyper-parameters by hand
		- Typically provides 
			- **Not** an answer
			- But a **suggested direction**
	- Try hyper-parameter tuning using `RandomizedSearchCV`
	- Then perform smaller grid for `GridSearchCV`

Once you've finished searching, its time to **compare** 
- Different models
	- `baseline_metrics`
	- `baseline_metrics_2`
	- `rs_metrics`
	- `gs_metrics`
- Compare using a plot
```
compare_results.plot.bar(
	figsize=(10, 8),
)
plt.show()
``` 

Our general approach
1. Try different hyper-parameters by-hand
2. Use `RandomizedSearchCV` to refine hand results
3. Use `GridSearchCV` to refine randomized search results
4. Iterate steps 1-3 as needed
5. Compare our different model metrics

