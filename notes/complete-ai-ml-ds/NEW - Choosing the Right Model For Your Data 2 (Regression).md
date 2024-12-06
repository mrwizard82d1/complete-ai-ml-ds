Be willing to try things even when uncertain
- Enables one to "train" your intuition

What if `Ridge`
- Did not work
- The resulting score was insufficient for our needs
- Try a **different** model

Back to the [machine learning map](https://scikit-learn.org/stable/machine_learning_map.html)!
- If "RidgeRegression" did not work well enough
- And if, perhaps, neither "Lasso" nor "ElasticNet" worked better
- Let's try "EnsembleRegressors"

An "ensemble" is
- A combination of smaller models to try 
- To make better predictions
- Than just a single model
- The ensemble models for `sklearn` can be found [here](https://scikit-learn.org/stable/modules/ensemble.html)

Repeat our typical steps
- Import
```python
from sklearn.ensemble import RandomForestRegressor
```
- Initialize our random number generator for reproducibility
- Create the data
```python
X = housing_df.drop('target', axis=1)
y = housing_df['target']
```
- Split into training and testing
```python
X_train, X_test, y_train, y_test = \ 
	train_test_split(X, y, test_size=0.2)
```
- Create, fit, and score our random forest model
```python
model = RandomForestRegressor()
model.fit(X_train, y_train)
model.score(X_test, y_test)
```

We increased our score!
- From 59.9%
- To 81.0%

Onto (eventually) picking a machine learning model for a classification problem
