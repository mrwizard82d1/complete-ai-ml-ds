Finished checking out correlation matrix
- Now is time to bring in machine learning

What's our problem?
- Defined at beginning (step 1)
- We have acquired data
- Now we're ready to evaluate
	- Our goal: "A minimum of 95% accuracy at predicting whether or not a patient had heart disease during the study"

Although not in the video, let's initialize our random number generator for reproducibility
```python
rng = np.random.default_rng(seed=42)
```

Let's split our data
- First into features (X) and labels (y)
```python
X = df.drop('target', axis=1)
y = df['target'}]
```
- Then split into training and test sets
```python
X_train, X_test, y_train, y_test = \
	train_test_split(
		X, y, test_size=0.2,
		random_state=np.random.integers(
			np.iinfo(np.int32).max
		)
	)
```

Now that we have our data split, what learning model(s) should we use?
- Consult the [Online machine learning model map](https://scikit-learn.org/stable/machine_learning_map.html)
	- The map suggests
		- K-neighbors Classifier
		- SVC Ensemble Classifiers
- But we "missing" one: Logistic Regression

Stay tuned for the next video!
