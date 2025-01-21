We left over noticing that
- Metrics in the classification report were calculated
- **Only** on our **single** test split
- We actually want these metrics calculated using **cross-validation**

Our goal: to calculate **using cross-validation**
- Accuracy
- Precision
- Recall
- F1 score
- To accomplish this goal, we will use the function, `cross_val_score()`.

We will score different metrics by 
- Setting the `scoring` parameter 
- Of the `cross_val_score()` function
- For logistic regression (in the video)
```python
gs_log_reg.best_params_
```
- Returns `{'C': 1.374..., 'solver': 'liblinear'}`
- For random forest classifier (in the workbook)
```python
rf_gs.best_params
```
- Returns 
```python
{
	'max_depth': 9,
	'min_samples_leaf': 19,
	'min_samples_split': 15,
	'n_estimators': 910,
}
```

We create a linear classifier with the best parameters:
```python
log_reg_clf = LogisticRegression(
	C=1.3738237958832638,
	solver='liblinear',
)
```

We now calculate our four metrics:
```python
# Accuracy
log_reg_cv_acc = cross_val_score(
	log_reg_clf, X_train, y_train, cv=5, scoring='accuracy',
)
log_reg_cv_acc = np.mean(log_reg_cv_acc)

# Precision
log_reg_cv_precision = cross_val_score(
	log_reg_clf, X_train, y_train, cv=5, scoring='precision',
)
log_reg_cv_precision = np.mean(log_reg_cv_precision)

# Recall
log_reg_cv_recall = cross_val_score(
	log_reg_clf, X_train, y_train, cv=5, scoring='recall',
)
log_reg_cv_recall = np.mean(log_reg_cv_recall)

# F1 score
log_reg_cv_f1 = cross_val_score(
	log_reg_clf, X_train, y_train, cv=5, scoring='f1',
)
log_reg_cv_f1 = np.mean(log_reg_cv_f1)
```
```python
cv_metrics = pd.DataFrame(
	'Accuracy': log_reg_cv_acc,
	'Precision': log_reg_cv_precision,
	'Recall': log_reg_cv_recall,
	'F1': log_reg_cv_f1,
)
cv_metrics.T.plot.bar(
	title='Cross-validated classification metrics',
	legend=False,
)
```

Repeat a similar process for my `RandomForestClassifier` results
```python
rf_gs.best_params

rf_clf = RandomForestClassifier(
	n_estimators=910,
	max_depth=9,
	min_samples_split=15,
	min_samples_leaf=19,
)

scorers = {
	'Accuracy': 'accuracy',
	'Precision': 'precision',
	'Recall': 'recall',
	'F1': 'f1',
}

# Define a helper function to perform cross-validation scoring and
# to calculate the mean across the results.
def cross_val_score_for(scorer):
	return np.mean(cross_val_score(
		rf_clf, 
		X_train,
		y_train,
		cv=5,
		scoring=scorer))

# Using cytoolz.dicttoolz.valmap()
rf_clf_scores = valmap(cross_val_score_for, scorers)
rf_clf_scores
```
- And plot these scores
```python
rf_clf_metrics = pd.DataFrame(rf_clf_scores, index=[0])

rf_clf_metrics.T.plot.bar(
	title='Cross-validated classification metrics (Random Forests)',
	legend=False,
)
plt.show()
```

And we see the "alternative" results
- But its tough from these plots to determine which approach is better
