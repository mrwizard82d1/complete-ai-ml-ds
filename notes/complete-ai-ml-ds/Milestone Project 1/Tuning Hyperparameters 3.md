Let's use hyperparameter tuning with `GridSearchCV`
- We'll try to improve our `LogisticRegression` model
	- Since that model performed best **in the video**
- Using `GridSearchCV`

We'll use slightly different ranges for our search
```python
log_reg_grid = {
	'C': np.logspace(-4, 4, 30),
	'solver': ['liblinear'],
}

gl_log_reg = GridSearchCV(
	LogisticRegression(
		random_state=np.iinfo(np.int32).max
	),
	param_grid=log_reg_grid,
	cv=5,
	verbose=True,
)

gl_log_reg.fit(X_train, y_train)
```
```python
gl_log_reg.score(X_test, y_test)
```
- With a result of 0.8033 (same as our original)

Although not in the video, I also tuned `RandomForestClassifier` using `GridSearchCV`
```python
rf_gs_grid= {
	'n_estimators': np.arange(850, 950, 25),
	'max_depth': [9, 10, 11],
	'min_samples_split': np.arange(14, 18, 1),
	'min_samples_leaf': np.arange(17, 21, 1),
}

rf_gs = GridSearchCV(
	RandomForestClassifier(
		random_state=rng.integers(np.iinfo(np.int32).max),
	),
	param_grid=rf_gs_grid,
	cv=5,
	verbose=True,
)
rf_gs.fit(X_train, y_train)
```
```python
rf_gs.best_params_
```
```python
rf_gs.fit(X_test, y_test)
```
- Fitting took quite awhile (5 min, 48s)
- Compare the scores

| Original | Random Search | Grid Search |
| -------- | ------------- | ----------- |
| 0.7541   | 0.8688        | 0.8524      |