The `predict()` method can be used on **regression** algorithms as well

Consider again our housing data frame, `housing_df`
```python
# Import the needed packages
from sklearn.ensemble import RandomForestRegressor

# Seed the random number generator for reproducibility
rng = np.random.default_rng(seed=42)

# Create the features and labels
X = housing_df.drop('target', axis=1)
y = housing_df['target']

# Split the data into training and test sets
X_train, X_test, y_train, y_test = \
	test_train_split(
		X,
		y,
		test_size=0.2,
		random_state=\
			rng.integers(np.iinfo(np.uint32).max)
	)

# Create, fit, and score the regressor
model = \
	RandomForestRegressor(
		random_state=\
			rng.integers(np.iinfo(np.uint32).max)
)
model.fit(X_train, y_train)
model.score(X_test, y_test)

# Make predictions
y_predictions = model.predict(X_test)
```

Let's look at our predictions
- `y_predictions[:10]`
- `np.array(y_test[:10])`

How might we used these two different results to evaluate our model
- Search 'sklearn regressions and tests'
- A couple of articles
	- [Evaluating a Random Forest Model](https://medium.com/analytics-vidhya/evaluating-a-random-forest-model-9d165595ad56)
	- [Random Forest Regression](https://towardsdatascience.com/random-forest-regression-5f605132d19d)

Let's compare our predictions with "the truth"
- Mean absolute error (MAE)
```python
from sklearn.metrics import mean_absolute_error
mean_absolute_error(y_test, y_predictions)
```

Let's add our predictions to `housing_df`
```python
housing_df['predictions'] = y_predictions
housing_df.head()
```
- Hmm... This code throws an exception
	- `len(y_predictions) == 4128`
	- `len(housing_df) == 20640`

How can we work around this "mismatch"?
- We need to think about this more

Stay tuned to the upcoming videos.
