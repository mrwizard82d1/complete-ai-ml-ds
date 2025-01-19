We've tuned our hyperparameters
- Now we want to create additional matrics

Evaluating our tuned machine learning classifier - beyond accuracy
- ROC curve and AUC score
- Confusion matrix
- Classification report
- Precision
- Recall
- F1-score
- ...and it would be great to use cross-validation where possible

We always want to compare **predictions** to our **true labels**
```python
y_preds = gs_log_reg.predict(X_test)
```

A reminder: the ROC curve compares the true positive and false positives rates
- True positive - model predicts 1; true label is 1
- False positive - model predicts 1; true label is 0
- A perfect model gets an AUC score of 1.0

Plot the ROC curve and calculate the AUC metric
- The video uses the function, `plot_roc_curve()`, that we defined earlier; however...
```python
RocCurveDisplay.from_estimator(gs_log_reg, X_test, y_test)
plt.show()
```
- For the higher metric in our workbook
```python
RocCurveDisplay.from_estimator(rs_rf, X_test, y_test)
plt.show()
```
- Remember that each `from_estimator()`  plot **includes** the AUC

Now let's plot our confusion matrix using `seaborn`
- Remember we use the corrected version from the previous note
```python
# Import Seaborn
import seaborn as sns
sns.set(font_scale=1.5) # increase the font size

def plot_conf_mat(y_test, y_preds):
	"""
	Plots a confusion matrix using `heatmap` from `seaborn`.
	"""
	fig, ax  plt.subplots(figsize=(3, 2))
	ax = sns.heatmap(
		confusion_matrix(y_test, y_preds),
		annot=True, # annotate the boxes
		cbar=False)

	plt.xlabel('Predicted label') # predictions on the x-axis
	plt.ylabel('True label') # true labels on the y-axis
)

plot_con_mat(y_test, y_preds)
plt.show()
```

in the next video, we'll tackle our cross-validation report _et al_
