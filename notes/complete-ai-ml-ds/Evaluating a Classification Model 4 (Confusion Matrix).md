Unfortunately, a confusing name

Definition: **Confusion Matrix**
- A _confusion matrix_ is a quick way to compare
	- The labels actually predicted by a model
	- The labels it was supposed to predict
- In other words, a _confusion matrix_ illustrates
	- Where the mode is "confused"

Let's get "hands on"
```python
from sklearn.metrics import confusion_matrix

y_predictions = clf.predict(X_test)

confusion_matrix(y_test, y_preductions)
```

H2 interpret the result of calling `confusion_matrix()`
- The `confusion_matrix()` function returns an array.
- Use `pd.crosstab()` to visualize
```python
pd.crosstab(y_test, y_predictions,
		    rownames=['Actual Labels'],
		    colnames=['Predicted Labels'])
```

How to interpret our confusion matrix?
- Predicted = 0, actual = 0 - True negatives
- Predicted = 0, actual = 1 - False negatives
- Predicted = 1, actual = 1 - True positives
- Predicted = 1, actual = 0 - False positives

H2 make our confusion matrix more visual?
- Use "seaborn's" `heatmap()`
- Note that this choice requires **installing seaborn**
```python
# Import `seaborn` for visualization
import seaborn as sns

# Set the font scale
sns.set(font_scale=1.5)

# Create a confusion matrix
conf_mat = confusion_matrix(y_test, y_predictions)

# Plot the confusion matrix using Seaborn
sns.heatmap(conf_mat)

plt.show()
```


A diversion: installing `seaborn` after the fact
- We **had not** installed `seaborn`
- I installed it from a shell using `conda install`
- Can install in a Jupyter notebook using:
```jupyter
# H2 install a conda package in a Jupyter notebook
import sys
!conda install --yes seaborn
```
- Remember that instructor needed to supply an additional argument:
- `--prefix {sys.prefix}`
