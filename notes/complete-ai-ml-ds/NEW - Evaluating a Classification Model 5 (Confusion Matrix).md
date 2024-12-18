We've seen a number of methods of evaluating classification methods
- A confusion matrix adds to our repertoire

Definition: confusion matrix
- A quick way to compare
	- The labels a model predicts with
	- The actual labels it was supposed to predict
- In essence, a confusion matrix illustrates where the **model** is "confused"

Documentation on "confusion matrix"
- [From sklearn](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.confusion_matrix.html)
- [From sklearn User Guide](https://scikit-learn.org/stable/modules/model_evaluation.html#confusion-matrix)
- [From W3 Schools](https://www.w3schools.com/python/python_ml_confusion_matrix.asp)

Our example code
```python
from sklearn.metrics import confusion_matrix

y_predictions = classifier.predict(X_test)

# Remember, `y_test` captures the **actual**
# results and `y_predictions` captures the 
# model predictions.
confusion_matrix(y_test, y_predictions)
```
- This action provides a result, but it is not very meaningful unless you are **already** familiar with a confusion matrix

The `pandas` package provides tools that provide additional insights into confusion matrices
- See the [pandas documentation](https://pandas.pydata.org/docs/reference/api/pandas.crosstab.html)
- Additionally, read this [Medium article](https://medium.com/geekculture/the-power-of-crosstab-function-in-pandas-for-data-analysis-and-visualization-6c085c269fcd) for a overview

Of course, let's see some code
```python
pd.crosstab(y_test, y_predictions,
		    rownames=['Actual Labels'],
		    colnames=['Predicted Labels'])
```

Interpreting the result
- The resulting chart displays both predicted and actual labels
- The "most valuable" numbers are along the diagonal
	- This results indicate
		- True negatives - (0, 0) - 25
		- True positives - (1, 1) - 26
- However, the numbers one typical cares about minimizing are **off the diagonal**
	- These values indicate where the model **did not** predict the actual (expected) value
	- In other words, the off-diagonal values indicate where our model **failed** to predict the actual results

Let's present this information more visually
![[Sklearn confusion matrix anatomy.png]]
- Although our picture only displays a 2x2 confusion matrix
	- One could expand this to NxN
		- However, as the number of dimensions increase
			- Our (intuitive) understand decreases

Let's make our confusion matrix a bit more colorful
- This requires a version of `sklearn` **greater than** 1.0
- If necessary,
```bash
conda activate complete-ai-ml-ds
conda update scikit-learn
# If using an environment file
conda env export > environment.yaml
```
- Remember, after updating a conda package
	- Restart your kernel
	- Run all cells:
- This update introduces two new functions
	- `ConfusionMatrixDisplay.from_estimator()`
	- `ConfusionMatrixDisplay.from_predictions()`A
- See [the documentation of ConfusionMatrixDisplay](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.ConfusionMatrixDisplay.html)


Using `ConfusionMatrixDisplay.from_estimator()`
```python
from sklearn.metrics import ConfusionMatrixDisplay

ConfusionMatrixDisplay.from_estimator(
	estimator=classifier,
	X=X,
	y=y,
)
```

Why is this plot different from our the plot in our previous lesson?
- We are passing all our data, `X` and `y` 
	- Instead of `X_test` and `y_test`

Let's look at `ConfusionMatrix.from_predictions()`
- **Requires** predictions to be **already available**
```
ConfusionMatrixDisplay.from_predictions(
	y_true=y_test,
	y_pred=y_predictions,
)
```
- To customize, see the documentation
	- For example, to change the colors