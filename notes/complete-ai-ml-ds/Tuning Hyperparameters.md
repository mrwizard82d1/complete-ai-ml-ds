Let's dive into hyperparameter tuning
- By hand

Now we need additional splits to support tuning
- Rule of thumb
	- 70 - 80%) used in training
	- 10% - 15% used in hyperparameter tuning
	- 10% - 15% used in testing

The most important concept in machine learning
![[Most-Important-Concept-In-ML.png]]
H2 determine what parameters to change?
- Read `RandomForestClassifier` documentation
- With some models, the notes will suggest hyperparameters to change
	- In the "Notes" section

In our learning, we will use
- `max_depth`
- `max_features`
- `min_samples_leaf`
- `min_samples_split`
- `n_estimators`

Since we will be creating a number of candidate models, let's create an evaluation function
```python
def estimate_preds(y_true, y_preds):
	accuracy = accuracy(y_true, y_preds)
	precision = precision(y_true, y_preds)
	recall = recall(y_true, y_preds)
	f1 = f1(y_true, y_preds)

	result = {
		'accuracy': round(accuracy, 2),
		'precision': round(precision, 2),
		'recall': round(recall, 2),
		'f1': round(f1, 2),
	}

	print(f'Accuracy: {accuracy * 100:.2f}')
	print(f'Precision: {precision:.2f}')
	print(f'Recall: {recall:.2f}')
	print(f'F1: {f1:2f}')

	return result
```

H2 create the train, validation, and test splits?
- Must perform split **manually**
- Here's my solution
```python
from sklearn.ensemble \
	import RandomForestClassifier

rng = np.random.default_rng(seed=42)

X = heart_disease.drop('target', axis=1)
y = heart_diseas['target']

X_train, X_other, y_train, y_other = \
	train_test_split(
		X, y, test_split=0.3,
		random_state=\
			rng.integers(
				np.iinfo(np.unit32).max
			)
	)

X_validate, X_test, y_validate, y_test = \
	train_test_split(
		X_other, y_other, 
		test_split=0.5,
		random_state=\
			rng.integers(
				np.iinfo(np.uint32).max
			)
	)

classifior = RandomForestClassifier(
	random_state=\
		rng.integers(
			np.iinfo(np.unit32).max
		)
)
```

- And here's Daniel's solution:
```python
from sklearn.ensemble \
	import RandomForestClassifier  
  
rng = np.random.default_rng(seed=42)  
  
# Shuffle the data  
heart_disease_shuffled = heart_disease.sample(  
    frac=1.0,  
	random_state=rng.integers(
	    np.iinfo(np.uint32).max
	)  
)  
  
X = heart_disease_shuffled.drop(
	'target', 
	axis=1
)  
y = heart_disease_shuffled['target']  
  
train_split_count = \
	round(
		0.7 * len(heart_disease_shuffled)
	)  
valid_split_count = \
	train_split_count + 
	round(
		0.15 * len(heart_disease_shuffled)
	)  
  
X_train = X[:train_split_count]  
y_train = y[:train_split_count]  
X_validate = \ 
	X[train_split_count:valid_split_count]  
y_validate = \ 
	y[train_split_count:valid_split_count]  
  
X_test = X[valid_split_count:]  
y_test = y[valid_split_count:]  
  
classifier = RandomForestClassifier(  
	random_state=rng.integers(
		np.iinfo(np.uint32).max
	)  
)
```

- And here's our "adjusted" fitting code
```python
classifier.fit(X_train, y_train)

y_preds = classifier.predict(X_validation)

baseline_metrics = \
	evaluate_predictions(
		y_test=y_validation,
		y_preds=y_preds
	)
baseline_metrics
```

Finally, let's evaluate our results with different estimators
```python
rng = np.random.default_rng(seed=42)

classifier_2 = RandomForestClassifier(
	n_estimators=200,
	random_state=rng.integers(
		np.iinfo(np.unit32).max
	)
)

classifier_2.fix(X_train, y_train)

y_preds_2 = classifier.predict(X_validation)

baseLine_metrics = \
	evaluate_predictions(
		y_test=y_validation,
		y_preds=y_preds
	)
baseline_matrics
```

In the video, the results are
- Slightly higher accuracy
- Higher precision
- Lower recall
- Same F1 score

Adjusting "by hand" takes **much work**
- Remember the rule: DRY

We'll use the in-built method
- `RandomizedSearchCV`

We'll use `RandomizedSearchCV` in the next videa
