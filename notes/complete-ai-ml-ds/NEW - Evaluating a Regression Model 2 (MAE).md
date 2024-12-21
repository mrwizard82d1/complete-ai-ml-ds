We've used the R^2 metric to score or models.
- Values
	- Near negative infinity indicate a poor match
	- Of 0 indicate a perfect match to the target mean
	- Of 1 indicate a perfect match to the target

Definition: **Mean absolute error (MAE)**
- The average of the absolute difference between predicted and actual values.

Code:
```python
from sklearn.metrics \
	import mean_absolute_error

# Evaluates how the model performs on the 
# **test** data
y_predictions = model.predict(X_test)

mae = mean_absolute_error(
	y_true=y_test,
	y_pred=y_predictions,
)
mae
```

What does the returned value, ~0.3347, mean?
- On average, each of our predictions is 0.3347
	- Too high or
	- Too low

Remember that the **difference** we calculate is actually in "units" of $100k

In the next video, we will investigate MSE - mean squared error.
