We calculated many numbers using `roc_curve()`
- But tough to understand an array of number

Let's write a function to plot ROC curves
```python
import matplotlib.pyplot as plt

def plot_roc_curve(fpr, tpr):
	# Plot the ROC curve
	plt.plot(fpr, tpr, 
			 color='orange', label='ROC curve')

	# Plot line with no predictive power
	# (AKA a "baseline")
	plt.plot([0, 1], [0, 1], 
			  color='darkblue',
			  linestyle='--',
			  label='Guessing')

	# Customize the plot
	plt.xlabel('False Positive Rate (FPR)')
	plt.ylabel('True Positive Rate (TPR)')
	plt.title ('Receiver Operating Characteristic' +
			   '(ROC) Curve')
	plt.legend()

	plt.show()
```

And then we run the function we just defined

Let's also look at the AUC score
```python
from sklearn.metrics import roc_auc_score

roc_auc_score(y_test, y_probs_positive)
```

Maximum AUC score is 1.0
- Similarly, "perfect" ROC curve is 
	- Perfectly vertical from y=0 to y=1
	- Perfectly horizontal from x=0 to x=1

Our next evaluation tool: a "confusion matrix"
