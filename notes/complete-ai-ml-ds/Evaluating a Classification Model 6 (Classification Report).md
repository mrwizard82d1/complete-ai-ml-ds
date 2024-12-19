Let's look at a "classification report"
- A **collection** of different metrics
- Compares actual and predicted values

Our code
```python
from sklearn.metrics import classification_report

print(classification_report(y_test, y_predictions))
```

Classification report anatomy
- Precision - Proportion of positive identifications (model predicted class 1) which were actually correct
	- Model with no **false positives** has precision 1.0
- Recall - Proportion of actual positives that were correctly classified.
	- Model with no **false negatives** has recall 1.0
- F1 score - Combination of precision and recall
	- Perfect model has an F1 score of 1.0
- Support - Number of samples on which each metric was calculated
- Accuracy - Model accuracy in decimal form. Perfect accuracy is 1.0
- Macro avg 
	- Short for macro average
	- The average precision, recall, and F1 score between classes. 
	- Macro average **does not** take class imbalances into account
		- If you **have class imbalances**, pay attention to this metric.
		- Our example is close to balanced
			- 32 examples resulted in false (0)
			- 29 examples resulted in true (1)
- Weighted avg
	- Short for weighted average
	- The weighted average precision, recall and F1 score  between classes
	- Each value is calculated with respect to the number of samples in each class
	- This metric favors any class outperforming the others (if any) because of more samples
- Remember, because our classes are fairly balanced (32-29), our macro average and weighted average are similar

When do I apply which metric?
- Our example: test 10,000 people for a disease. But only one has it.
- In this situation, **all** the metrics become valuable
	- We'll focus on
		- Precision
		- Recall

For example,
```python
disease_true = np.zeros(10000)
disease_true[0] = 1 # True

# Our model predicts 0 (False) for **everyone**
disease_predictions = np.zeros(10000)

pd.DataFrame(
	classification_report(
		disease_true,
		disease_predictions,
		output_dict=True
	)
)
```
- Note that the argument, `output_dict=True`, prevents an error
	- I think due to "Precision is ill-defined" message in the warning
- In this situation (a single true sample)
	- Accuracy is 99.99%
	- But macro average is about 50%
	- Illustrates that it is **hard** to find this pattern
- I wonder, "Would a Bayesian model" yield similarly difficult to interpret results

See the [Scikit Learn metrics and scoring section](https://scikit-learn.org/stable/modules/model_evaluation.html) for a 
- List of strictly consistent scoring functions
- A list of [string name scorers](https://scikit-learn.org/stable/modules/model_evaluation.html#string-name-scorers)
- "Lists" of [classification metrics](https://scikit-learn.org/stable/modules/model_evaluation.html#classification-metrics) (to measure classification performance)

In the next section, we'll dive into more specific regression model evaluation metrics
