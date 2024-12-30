We've seen how to tune parameters by hand
- Conclusion: tough work
- Answer: `RandomizedSearchCV`

Here's our code
```python
from sklean.model_selection import (
	RandomizedSearchCV,
)

# The "grid" of parameters 
# with their values to search
grid = {
	'n_estimators': [10, 100, 200, 500, 1000, 1200],
	'max_depth': [None, 5, 10, 10, 30],
	# NOTE: In scikit-learn version 1.1, the 
	# default value of `max_features` was 
	# changed from 'auto' to 'sqrt'. From
    # the error message that occurred when
    # I included 'auto', I think 'auto' 
    # has been removed.
    # 'max_features': ['auto', 'sqrt'],
	'max_features': ['sqrt', 'log2', None],
	'min_samples_split': [2, 4, 6],
	'min_samples_leaf': [1, 2, 4],
}

rng = np.random.default_rng(seed=42)

X = heart_disease_shuffled.drop('target', axis=1)
y = heart_disease_shuffled['target']

X_train, X_test, y_train, y_test = train_test_split(
	X, y, test_size=0.2,
	random_state=rng.integers(
		np.iinfo(np.uint32).max
	)
)

classifier = RandomForestClassifier(
	X, y, test_size=0.2,
	random_state=rng.integers(
		np.iinfo(np.uint32).max
	),
	n_jobs=1,
)

# NOTE: Because we are using cross-validation,
# we need **not** create a validation split
rs_classifier = RandomizedSearchCV(
   estimator=classifier,
   param_distribution=grid,
   n_iter=10, # number of models to try
   cv=5,
   verbose=2
)

rs_classifier.fit(X_train, y_train)
```

Once we have  fit the model, H2 determine best parameters?
```python
rs_classifier.best_params_
```

Once we have **found** the best hyperparameters,
- The `predict()` method will **use them** automagically
```python
rs_y_preds = rs_classifier.predict(X_test)

rs_metrics = evaluate_predictions(y_test, rs_y_preds)
```

**NOTE**: we **did not** see any improvement
- Perhaps we can change the number of iterations

But we will move on to learn about `GridSearchCV`
