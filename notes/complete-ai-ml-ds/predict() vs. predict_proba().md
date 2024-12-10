We've seen one way, `predict()`, to evaluate our models
- Now we'll consider another `predict_proba()`

Consult the documentation
- `predict_proba()` is "probability estimates"
- The returned estimates for all classes are ordered by the **class labels**

Our rule: run the code
- `clf.predict_proba(X_test)`

Returns much data so... reduce
- `clf.predict_proba(X_test[:5])`
- Returns an `np.array` of 5 samples
	- Each item is an array of **two** numbers
		- Because we only have two labels: 0 or 1
		- Each item is a **probability** of the label
			- 0 or
			- 1
- In other words, it returns a probability of each and every label
- Can use `clf.predict_proba()` on some other algorithms:
	- See [Probability calibration](https://scikit-learn.org/stable/modules/calibration.html) in `scikit-learn` documentation

Contrast `predict()` and `predict_proba()`
- `predict()` gives a **single label**
- `predict_proba()` give a **probability** for **each label**

Have a look at how to understand the "strength" of a regression model
