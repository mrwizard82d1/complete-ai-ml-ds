Time to investigate our third mechanism for evaluation

Let's use Scikit-Learn **functions** to evaluate models (or estimators)
```python
from sklearn.metrics import (
	 accuracy_score, precision_score,
	 recall_score, f1_score
from sklearn.ensemble \
	import RandomForestClassifier
from sklearn.model_selection \
	import train_test_split

X = heart_disease.drop('target', axis=1)
y = heart_disease['target']

X_train, X_test, y_train, y_test = \
	train_test_split(
		X, y, test_size=0.2,
		random_state=\
			rng.integers(
				np.iinfo(np.unit32).max
			)
	)

classifier = RandomForestClassifier(
	random_state= rng.integers(
		np.iinfo(np.unit32).max			
	)
)
classifier.fit(X_train, y_train)

y_predictions = classifier.predict(X_test)
```

And then calculate our metrics
```python
clf_accurancy = accurancy_score(
	y_true=y_test,
	y_pred=y_predictions)

clf_precision = precision_score(
	y_true=y_test,
y_pred=y_predictions
)

clf_recall = recall_score(
	y_true=y_test,
	y_pred=y_predictions
)
```

And similarly for regression
```python
from sklearn.metrics import (
	r2_score, 
	mean_absolute_error ,
	mean_square_error,
)
from sklearn.ensemble import (
	RandomForestRegressor,
)
from sklean.model_selection import (
	train_test_split,
)

X = housing_df.drop('target', axis=1)
y = housing_df['target']

X_train, X_test, y_train, y_test = \
	train_test_split(
		X, y, test_size=0.2,
		random_state=\
			rng.integers(
				np.iinfo(np.uint32).max
			)
	)

regressor = RandomForestRegressor(
	random_state=\
		rng.integers(
		np.iinfo(np.uint32).max
	)
)
y_predictions = regressor.fit(X_test)
```

```python
model_r2 = r2_score(
	y_true=y_test,
	y_pred=y_predictions,
)
model_mae = mean_absolute_error(
	y_true=y_test,
	y_pred=y_predictions,
)
model_mse = mean_square_error(
	y_true=y_test,
	y_pred=y_predictions,
)
```

