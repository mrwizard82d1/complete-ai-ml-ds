Now the "magic" truly begins

### Random Forest model deep dive

See [[Random Forest Resources]]

Although we've not made **explicit** predictions,
- They have occurred "behind the scenes"
	- For example, `clf.score()` 
		- Make predictions
		- Compares the predicted y-values to `y_test`

Use a trained model to make predictions
- 2 main ways to make predictions
	- `predict()`
	- `predict_proba()`

What should `predict` use to make a prediction?
- Since our model was trained (and tested) with the value `X`,
	- It should use `X` to make predictions
- Trying to "predict" using an arbitrary `np.array`
	- Raises a `ValueError`

We can score a model using many different techniques
- And producing the **same** result

```python
y_predictions = clf.predict(X_test)
np.mean(y_predictions == y_test)
```

- `clf.score(X_test, y_test)`
- `accuracy_score(y_test, y_predictions)`

Now let's look at `predict_proba()` (in the next video)
