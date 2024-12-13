We've seen how to evaluate our fit using `score()`
- Uses a different algorithm appropriate to our model

Evaluating a model using the `scoring` parameter
```python
from sklearn.model_selection import cross_val_score
```

Now lets run a classifier
```python
from sklearn.ensemble import RandomForestClassifier

rng = np.random.default_rng(seed=42)

X = heart_disease.drop('target', axis='columns')
y = heart_disease['target']

X_train, X_test, y_train, y_test = \
	train_test_split(
		X, y, test_size=0.2,
		random_state=rng.integers(
			np.iinfo(np.uint32).max
		)			
	)

classifier = RandomForestClassifier(
	X, y, test_size=0.2,
	random_state=rng.integers(
		np.iinfo(np.uint32).max
	)
)
classifier.fit(X_train, y_train)
```

Calculate the typical `score()` and the cross-fit score and compare
```python
classifier.score(X_test, y_test)

# This evaluation takes **all** the features and labels not the splits
cross_val_score(classifier, X, y, cv=5)
```

The following diagram describes the differences between
- Normal train and test split
- 5-fold cross validation
![[Compare Cross-Validation and Normal Train-Test Split.png]]

What's the value of cross-validation?
- Normal train and test splits rely on the (random) split to be "good"
	- It may not!
		- For example, suppose `train_test_split()` happens to give us really good training data 
			- Our result will work really well
			- **But may not** perform so well on **real world data**
		- Similarly, if `train_test_split()` **does not** yield really good training data
			- Our score may be "good" 
			- But the model **may not** generalize to other data

Let's compare the result of `score()` with the **mean** of our cross-validation score
```python

rng = np.random.default_rng(seed=42)

clf_single_score = clf.score(X_test, y_test)

clf_cross_val_score = np.mean(
	cross_val_score(clf, X, y, cv=5)
)

clf_single_score, clf_cross_val_score
```

Let's look at the `scoring` parameter
- By default, `scoring=None`
- If `scoring=None`
	- The score uses the default scoring parameter of our estimator
	- In our case, the default is mean accuracy
		- `help(clf.score)` (scroll to bottom of documentation)
