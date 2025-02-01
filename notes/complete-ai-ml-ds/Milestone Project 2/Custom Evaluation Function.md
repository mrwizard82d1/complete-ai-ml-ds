We've split our data

Previously, we used the `score()` function to evaluate our model
- It uses the coefficient of determination
- However, the evaluation for the "competition" is
	- RMSLE - Root mean squared log error

We've previously discussed how to measure errors for regression problems
- R^2 (r-squared)
- MAE - mean absolute error
- MSE - mean squared error
- RMSE - root mean squared error
- But **not** RMSLE

Let's look at what's available from `sklearn`
- Previously `sklearn` only offered the 'neg_mean_squared_log_error'
- In the latest version I've also found 'neg_root_mean_squared_log_error'
	- In theory, I need not 
		- Perform the additional transformation that Daniel describes in the video
		- But I will
- I will also compare it to the value calculated natively by `sklearn`
- Remember our guide to regression metrics:
![[RegressionMetricGuidance.png]]

Here's the evaluation function I will use:
```python
from sklearn.metrics import (
	mean_absolute_error,
	mean_squared_log_error, 
	root_mean_squared_log_error,
)


def rmsle(y_test, y_pred):
	return np.sqrt(mean_squared_log_error(y_test, y_pred))


# Create a comparison function to compare different metrics
def show_scores(model):
	train_predictions = model.predict(X_train)
	validation_predictions = model.predict(X_valid)

	scores = {
		'Training MAE': mean_absolute_error(y_train, train_predictions)
		'Validation MAE':
			mean_absolute_error(y_valid, validation_predicitions)
		'Training custom RMSLE': 
			rmsle(y_train, train_predictions)
		'Validation custom RMSLE':
			mean_absolute_error(y_valid, validation_predicitions)
		'Training RMSLE': 
			root_mean_squared_log_error(y_train, train_predictions)
		'Validation RMSLE':
			root_mean_squared_log_error(y_valid, validation_predicitions)
		'Training R^2': 
			r2_score(y_train, train_predictions)
		'Validation R^2':
			r2_score(y_valid, validation_predicitions)
	}
	return scores
```

We've accomplished much - but we'll test it in the next video
