Our last requirement: feature importance

Our definition
- Feature importance is another way of asking
	- "Which features contributed most to the outcomes of the model?"
	- "How did they contribute?"

But how do we **find feature importance**?
- Depends on the model we use
- A Google search
	- For example, "How to find feature importance using logistic regression?"
- An example search term
	- "(MODEL NAME) feature importance"
- I found [this post](https://linguisticmaz.medium.com/feature-importance-in-python-e3eb0c458b1c) useful to explain candidate approaches for different models

We perform a number of steps
- Find the best hyperparameters
```python
gs_log_reg.best_params_
```
- Create and fit a model with the best hyperparameters
```python
clf_log_reg = LogisticRegression(
	C=1.3738237958832638,
	solver='liblinear',
)
clf_log_reg.fit(X_train, y_train)
```
- Display the `LogisticRegression` coefficients
```python
clf_log_reg.coef_
```
- This expression returns an `np.ndarray` of coefficients
	- One for each column
```python
clf_log_reg.coef_.size, len(df.columns)
```

Let's match the coefficients of features to columns
```python
feature_dict = dict(zip(df.columns, list(clf_log_reg.coef_[0])))
feature_df = pd.DataFrame(feature_dict, index=[0])
feature_df.T.plot.bar(
	title='Feature Importance',
	legend=False,
)
```

The largest correlation is for the column, 'sex'
- Let's investigate this correlation
```python
pd.crosstab(df['sex'], df['target'])
```
- The result of this cross tab does not seem to bear out our hypothesis
- However,
	- If, for a given value of sex, 
		- One considers the ratio of "heart disease" to "no heart disease"
		- One sees that for females (`sex == 0`)
			- The ratio is about 3
		- And the same ratio for males (`sex == 1`)
			- The ratio is slightly less than 1 (about 0.82)

Let's look at a **positive** coefficient
- For example, `cp` or `slope`
```python
pd.crosstab(df['slope'], df['target'])
```
- Remember our definition
- slope: the slope of the peak exercise ST segment  
	- 0: Upsloping
	- 1: Flatsloping
	- 2: Downsloping
- Use our domain experts to **validate our findings**

What might we be missing? We consider this question in the next video.

Oops. Forgot to perform a similar analysis for our `RandomForestClassifier`
```python
# Best parameters
rf_gs.best_params_

# Create our classifier with the best hyperparameters
clf_rf = RandomForestClassifier(
	n_estimators=910,
	max_depth=9,
	min_samples_split=15,
	min_samples_leaf=19,
)
clf.fit(X_train, y_train)
```

One analogue to `LinearRegression.coef_` is  
- `RandomForestClassifier.feature_importances_`
```python
importances = clf_rf.feature_importances
```

We can plot the impurity-based importance
```python
fig, ax = plt.subplots()
forest_importances = pd.Series(importances)
ax.set_title('Feature Importances using MDI')
ax.set_ylabel('Mean Decrease in Impurity')

fig.tight_layout()
plt.show()
```

The article, [Feature importances with a forest of trees](https://scikit-learn.org/1.6/auto_examples/ensemble/plot_forest_importances.html), describes two metrics
- Mean decrease in impurity
- Feature permutation

Here is a similar analysis using feature permutation (which takes a few seconds)
- The calculation
```python
from sklearn.inspection import permutation_importance

result = permutation_importance(
	clf_rf, X_test, y_test, n_repeats=10, n_jobs=2
)
```
- The plot
```python
fig, ax = plt.subplots()
forest_importances.plot.bar(yerr=result.importances_std, ax=ax)
ax.set_title('Feature Importances using Permutation on Full Model')
ax.set_ylabel('Mean Accuracy Decrease')
fig.tight_layout()
plt.show()
```
