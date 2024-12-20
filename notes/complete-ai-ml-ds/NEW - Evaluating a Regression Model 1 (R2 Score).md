Let's get into regression model evaluation metrics

Regression model evaluation metrics
- [Regression metrics by name](https://scikit-learn.org/stable/modules/model_evaluation.html#string-name-scorers)
- [Metrics details](https://scikit-learn.org/stable/modules/model_evaluation.html#regression-metrics)
	- Homework reading

Metrics we will cover
- R^2 (pronounced r-squared) or coefficient of determination
- Mean absolute error (MAE)
- Mean squared error (MSE)

We will again run our regression model
```python
from sklearn.ensemble \
	import RandomForestRegression

rng = np.random.default_rng(seed=42)

X = housing_df.drop('target',
				    axis='columns')
y = housing_df['target']

X_train, X_test, y_train, y_test = \
	train_test_split(
		X, y, test_size=0.2,
		random_state=rng.integers(
			np.iinfo(np.int32).max
		)
	)

model = RandomForestRegressor(
	random_state=rng.integers(
		np.iinfo(np.int32).max
	)
)
model.fit(X_train, y_train)
```

Once we have fit the model, we score it using the test data
```python
model.score(X_test, y_test):
```

Definition - coefficient of determination (R^2)
- The proportion of the variation in the **dependent** variable that is **predictable** from the independent variable - [Wikipedia](https://en.wikipedia.org/wiki/Coefficient_of_determination)
- Ranges from
	- 0.0 no relationship
	- 1.0 a "perfect" relationship

We can import the `r2_score` directly
```python
from sklean.meatrics import n2_score

# Fill an array with `y_test.mean()`
y_test_mean = np.full(
	len(y_test),
	y_test.mean()
)

r2_score(y_true=y_test,
		 y_pred=y_test_mean)
```
- Since the R^2 score evaluates the difference from the mean, we expect an R^2 score of 0
- And that's what we observe

For homework, try to evaluation our model using
- Mean absolute error (MAE)
- Mean squared error (MSE)