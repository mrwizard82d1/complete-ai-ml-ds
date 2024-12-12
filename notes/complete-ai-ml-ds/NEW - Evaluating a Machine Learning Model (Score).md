In last video, saw
- H2 use `predict()` on regression models

Three ways to evaluate `scikit-learn` models/algorithms/estimators
- Estimator's built-in `score()` method
- The `scoring` parameter
- Problem-specific metric functions

Homework
- Review [Metrics and scoring](https://scikit-learn.org/stable/modules/model_evaluation.html)

Evaluating a model with the `score` method
```python
# Use `RandomForestClassifier` to "experiment"
from sklearn.ensemble import RandomForestClassifier

# Use a well-known random number generator "seed"
rng = np.random.default_rng(seed=42)

# Create features (`X`) and labels (`y`)
X = heart_disease.drop('target', axis=1)
y = heart_disease['target']

# Split into training and test sets
X_train, X_test, y_train, y_test =  train_test_split(
	X, y, test_size=0.2, random_state=\
		rng.integers(np.iinfo(np.uint32).max)
)

# Create, fit, and score a model
classifier = RandomForestClassifier(
	random_state=\
		rng.integers(np.iinfo(np.uint32).max)
)
classifier.fit(X_train, y_train)
classifier.score(X_test, y_test)
```

Remember, executing `score` on the **training** data may result in a score of **1.0**
- `clf.score(X_train, y_train)`
- The `score()` method reflects **mean accuracy**
- Our model has been trained on the **training data** 

Scoring our model on the **test** data does not provides as high a score
- `clf.score(X_test, y_test)`
	- Results in ~ 0.8033
- Always be skeptical of 100% scores