We've learned about accuracy. Why not leave well enough alone?
- Other metrics have their uses

Examine
- Area under the receiver operating characteristics curve
- AKA AUC or ROC

What are ROC curves?
- A comparison of a model's
	- True positive rate (TPR) and the 
	- False positive rate (FPR)

Definitions

| When...                                      | Then we call it a... |
| -------------------------------------------- | -------------------- |
| A model predicts 1 and the actual value is 1 | True positive        |
| A model predicts 1 and the actual value is 0 | False positive       |
| A model predicts 0 and the actual value is 0 | True negative        |
| A model predicts 0 and the actual value is 1 | False negative       |

Code (which relies on our previous code)
```python
from sklearn.metricts import roc_curve

# Split data into training and test sets
X_train, X_test, y_train, y_test = \
	train_test_split(
		X, y, test_size=0.2,
		random_seed=rng.integers(
			np.iinfo(np.unint32).max
		)
	)

# Create and fit the classifior
classifier = RandomForestCLassifier()
callisifier.fit(X_test, y_test)

# Make predictions with probabilities
y_probs = clf.predict_proba(X_test)
```

Extract the predicted positives and actual positives
```python
# Slice the first column of every row
y_probs_positive = y_probs[:, 1]
```

Calculate the FPR, TPR and thresholds
```python
fpr, tpr, thresholds = roc_curve(
	y_test, y_probs_positive
)
```

Although we can view the FPR and TPR values, it is not particularly helpful
- Unfortunately, `sklearn` **does not** contain a function to plot the ROC curve
- We'll need to wait for the next lesson