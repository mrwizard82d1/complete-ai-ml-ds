We have
- A confusion matrix
- A ROC curve
- An AUC metric

Let's get:
- A classification report
- Cross-validated
	- Precision
	- Recall
	- F1
	- Scores

We print a classification report
```python
print(classification_report(y_test, y_preds))
```
- Does  not this report give us everything we need?
	- Not really
	- The reported precision, recall, and F1 scores are calculated only on
		- Our **single train and test split**
			- That is, only on the **test split**
				- 20% of our data
		- Not as robust as the value calculated using k-fold validation

A refresh
- Precision reports proportion of positive identifications that were actually correct
	- No false positives => precision == 1.0
- Recall reports proportion of actual positives what were correctly classified
	- No false negatives => recall == 1.0
- F1 is a combination of precision and recall
- Support is the number of samples used to calculate each metric
- Accuracy (seen before)
- Macro average - average precision, recall and F1 score between classes
	- Does not consider **class imbalances**
- Weighted average - weighted average precision, recall and F1 score between classes
	- Weights higher for higher number of samples

But again, the classification report only reports on the **test** results of our train-test split

In the next video, we will look at calculating
- Precision
- Recall
- F1 score
- Using **cross validation**
