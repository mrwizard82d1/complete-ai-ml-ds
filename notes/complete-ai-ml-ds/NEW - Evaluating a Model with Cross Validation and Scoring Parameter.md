We've investigated many scoring options
- But we will finally use the `scoring` parameter

Our sample set up code for classification
```python
from sklearn.model_selection \
	import cross_val_score


# Begin with `RandomForestClassifier`
from sklearn.ensemble \
	import RandomForestClassifier

rng = np.random.default_rng(seed=42)

X = heart_disease.drop('target', 
					   axis='columns')
y = heart_disease('target')

classifier = RandomForestClassifier(
	random_seed=rng.integers(
		np.iinfo(np.unit32).max
	)
)
```

Cross-validation accuracy
```python
# Remember, if `scoring = None`, the default
# scoring evaluation metric is used. For
# classification models, the `accuracy` 
# metric is used.
cv_acc = cross_val_score(
	 classifier, X, y, scoring=None,
)
```

What if we want to **change** the scoring method?
```python
# Explicitly invoke the default scoring method
cv_acc = cross_val_score(
	 classifier, X, y, scoring='accuracy',
)
```

Let's try it with the 'precision' scoring metric
```python
cv_precision = cross_val_score(
	 clasifier, X, y, scoring='precision'
)
```

The value of cross-validation
- Notice that the `cv_precision` number is
	- Not only **different** from the `cv_acc` number
	- But also has a **different range** of values
- Because cross-validation provides multiple values
	- The reported values give us a better idea of the overall fit

Let's try it with 'recall'
```python
cv_recall = cross_val_score(
	classifier, X, y, scoring='recall',
)
```

Our model appears to do better on 'recall' than on other metrics
- The five cross-validation values have a smaller range than for other metrics

Our set up code for regression
```python
from sklearn.model_selecetion \
	import cross_val_score
from sklearn.ensembles \
	import RandomForestRegressor

# Initialize our random number generator
# for repeatability
rng = np.random.default_rng(seed=42)

X = housing_df.drop('target', axis='columns')
y = housing_df['target']

regressor = RandomForestRegressor(
	random_state=\
		rng.integer(np.iinfo(np.uint32).max)
)
```

Let's calculate the ${R}^2$ metric
```python
cv_r2 = cross_val_score(
	regressor, X, y, cv=5, scoring=None,
)
cv_r2
```

Let's try the mean absolute error (MAE)
```python
cv_mae = cross_val_score(
	regressor, X, y, cv=5, 
	scoring='neg_mean_absolute_error',
)
```

And the mean squared error
```python
cv_mse = cross_val_score(
	regressor, X, y, cv=5,
	scoring='neg_mean_squared_error',
)
```

**NOTE**: the metrics for MAE and MSE
- Are both **negative**
- The reason for this is consistency
	- From [the documentation](https://scikit-learn.org/stable/modules/model_evaluation.html#string-name-scorers)
		- ".All scorer objects follow the convention that **higher return values are better than lower return values**. Thus, metrics which measure the distance between the model and the data, like metrics.mean_squared_error, are available as 'neg_mean_squared_error' which return the negated value of the metric."
