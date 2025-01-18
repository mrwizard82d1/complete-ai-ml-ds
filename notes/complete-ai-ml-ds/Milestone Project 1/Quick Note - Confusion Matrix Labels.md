In the next video, we reverse the x- and y-axis labels

Here is the correct code:
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
```
- That is,
	- x-axis has model predictions
	- y-axis has true labels
