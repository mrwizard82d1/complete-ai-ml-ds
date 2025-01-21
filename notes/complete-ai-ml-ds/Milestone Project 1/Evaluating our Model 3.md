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
