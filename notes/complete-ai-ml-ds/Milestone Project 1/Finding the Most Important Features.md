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
clf = LogisticRegression(
	C=1.3738237958832638,
	solver='liblinear',
)
clf.fit(X_train, y_train)
```
- Display the `LogisticRegression` coefficients
```python
clf.coef_
```
- This expression returns an `np.ndarray` of coefficients
	- One for each column
```python
clf.coef_.size, len(df.columns)
```

Let's match the coefficients of features to columns
```python
feature_dict = dict(zip(df.columns, list(clf.coef_[0])))
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
