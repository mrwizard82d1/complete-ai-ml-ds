We've now built a model
- Others will ask, "Which of these features are **the most important**?"

Feature importance
- Seeks to determine which attributes
- Were **most important** in predicting (affecting)
- The **target variable**
- In our experiment, the target variable was `SalePrice`

We might search
- "random forest regressor feature importance"
- From the scikit-learn User Guide:
	- https://scikit-learn.org/stable/auto_examples/ensemble/plot_forest_importances.html

Let's use the `feature_importances_` attribute
```python
ideal_model.feature_importances_
```
- Returns an instance of `np.array` of length 102
	- That is, one item for each column in our features

Difficult to "grok" an array. Let's plot the importances.
```python
def plot_features(columns, importances, n = 20):
	df = (pd.DataFrame({
		'features': columns,
		'feature_importances': importances
	}).sort_values('feature_importances', ascending=False)
	  .reset_index(drop=True))

fig, ax = plt.subplot()
ax.barh(df['features'][:n], df['feature_importances'][:n])
ax.set_ylabel('Features')
ax.set_xlabel('Feature importance)
ax.invert_yaxist(

plt.show()
```

To understand this plot,
- For a column of interest,
	- Consult our "data dictionary" 
	- View the `value_counts()` of a column of interest
		- Of the training data frame (`X_train['ProductSize'].value_counts()`)
		- Of the original data frame (`df['ProductSize'].value_counts()`)

Review our feature importance plot with the client / user / domain expert
- Both to ensure that we have not "done something stupid"
- Surface insights
- Gain additional research directions

**Question to finish**:
- Why might knowing the feature importances of a trained machine learning model by helpful?

**Final challenge**
- What other machine learning models could you try on our dataset?
- See [Online machine learning model map](https://scikit-learn.org/stable/machine_learning_map.html)
- Try looking at other classifiers
	- [CatBoost](https://medium.com/@pwrxndr/catboost-classifier-a-simple-guide-for-everyone-48a2e3897251)  
	- [CatBoost for Regression](https://towardsdatascience.com/catboost-regression-in-6-minutes-3487f3e5b329/)  
	- [XGBoost](https://medium.com/@bravinwasike18/dive-into-xgboost-and-scikit-learnmachine-learning-with-xgboost-and-scikit-learn-17e2cf54f3a3)  
	- [XGBoost for Regression](https://machinelearningmastery.com/xgboost-for-regression/)
