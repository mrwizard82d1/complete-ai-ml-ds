Learn (again) using `RandomForestRegressor`
```python
from sklearn.ensembel import RandomForestRegressor

rng = np.random.default_rng(seed=42)

X = housing_df.drop('target', axis='columns')
y = housing_df['target']

X_train, X_test, y_train, y_test = \
	train_test_split(
		X, y, test_size=0.2,
		random_state=\
			rng.integer(np.iinfo(np.uint32).max)
	)

regressor = RandomForestRegressor(
	random_state=\
		rng.integer(np.iinfo(np.unit32).max)
)
regressor.fit(X_train, y_train)
```

We score both our training and test data
```python
regressor.score(X_train, y_train)
regressor.score(X_test, y_test)
```

