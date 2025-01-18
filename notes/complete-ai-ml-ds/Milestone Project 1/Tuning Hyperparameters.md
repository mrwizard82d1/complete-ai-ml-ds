We tuned KNN **by hand**
- Only tuned 1 parameter
- Tuning many parameters by hand is **tedious**
- Result: no longer pursue KNN

Hyperparameter tuning with `RandomizedSearchCV`
- One can search, for example, 
	- "How to tune a logistic regression machine learning model in Python"
- We'll assume we've done that work

Search the documentation
- But **try things out to learn**

Remember, k-fold cross-validation
- Splits the data into `k` different sets
	- Each set takes `1/k` samples and sets them aside for validation
- Loop over `k` different splits
	- Train data on `4/k` samples
	- Test data on `1/k` samples
	- Repeat until trained and tested on all `k` splits
	- Report results of all `k` runs
- `RandomizedSearchCV` will
	- Randomly select a set of hyperparameters
	- Perform a k-fold cross validation using those parameters
	- Repeat until finished
	- Report results

Set up grids for
- `LogisticRegression`
- `RandomForestClassifier`
```python
log_reg_grid = {
	'C': np.logspace(-4, 4, 20),
	'solver': ['liblinear'],
}

rf_grid = {
   'n_estimators': np.arange(10, 1000, 50),
   'max_depth': [None, 3, 5, 10],
   'min_samples_split': np.arange(2, 20, 2),
   'min_samples_leaf': np.arange(1, 20, 2),
}
```

