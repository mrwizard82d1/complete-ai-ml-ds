Let's see some other important evaluation metrics
- Accuracy
- Area under ROC curve
- Confusion matrix
- Classification report

Import the classification model evaluation metrics
```python
from sklearn.model_selection import cross_val_score
from sklearn.ensemble import RandomForestClassifier

rng = np.random.default_rng(seed=42)

X = heart_disease.drop('target', axis='columns')
y = heart_disease['target']

# Because we are investigating **accuracy**, we 
# actually **do not need** to split our data into
# training and test sets.
# X_train, X_test, y_train, y_test = \
#   train_test_split(
#		X, y, test_size=0.2,
#		random_state=rng.integers(
#			np.iinfo(np.uint32).max
#		)
#	)

classifier = RandomForestClassifier(
	random_state=rng.integers(
		np.iinfo(np.uint32).max
	)
)
cross_val_score(classifier, X, y, cv=5)

print('Heart Disease Classifier' 
	  'Cross-Validated Accuracy:'  
	  f' {np.mean(cross_val_score) * 100:.2f}')
```
