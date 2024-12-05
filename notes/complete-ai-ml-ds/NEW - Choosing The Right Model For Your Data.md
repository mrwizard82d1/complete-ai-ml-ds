Our focus: 
- Step 2
	- Choosing the right estimator/algorithm/model for your problem

Some things to note:
- The package, `sklearn`, refers to machine learning models and algorithms as _estimators_.
	- A _classifier_ is one type of estimator
		- AKA a _classification model_
	- A _regressor_ is another type of estimator
		- AKA a _regression model_
- Classification problem - predicting a category
	- For example: heart disease or not heart disease
	- Sometimes you see the term `clf`
		- A TLA for **classifier** 
		- Used as a **classification estimator**
- Regression problem - predicting a **number**
	- For example, the selling price of a car

Scikit-learn offers many **different** estimators
- See the [`sklearn` machine learning model map](https://scikit-learn.org/stable/machine_learning_map.html)
- This diagram provides a
	- "Decision tree" that allows one 
	- To determine the appropriate algorithm to use
	- To solve the problem at hand

| If you are...                                                                                       | Then...                                                                                                   |
| --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| - Working on a machine learning problem<br>- Looking to use `sklearn`<br>- Unsure what model to use | Use the `sklearn` [machine learning model map](https://scikit-learn.org/stable/machine_learning_map.html) |

Daniel, where are you getting these ideas from?
- The `sklearn` documentation on [datasets](https://scikit-learn.org/stable/datasets.html)
	- [Toy datasets](https://scikit-learn.org/stable/datasets/toy_dataset.html)
	- [Real world datasets](https://scikit-learn.org/stable/datasets/real_world.html)
	- [Generated datasets](https://scikit-learn.org/stable/datasets/sample_generators.html)
	- [Loading other datasets](https://scikit-learn.org/stable/datasets/loading_other_datasets.html)

Get the [California Housing dataset](https://scikit-learn.org/stable/datasets/real_world.html#california-housing-dataset)
```python
from sklearn.datasets import fetch_california_housing
housing = fetch_california_housing()
housing
```

Let's turn our dataset into a `DataFrame` 
```python
housing_df = \
	pd.DataFrame(housing['data'],
				 columns=housing['feature_names'])
housing_df
```

Add the target column(s)
```python
housing_df[housing.target_names[0]] = housing.target
housing_df
```

Rename the target column to 'target'
```python
housing_df = housing_df.rename({'MedHouseVal': 'target'}, axis=1)
housing_df
```

Split data frame into features and target (`X` and `y`)
- Import the appropriate algorithm
	- Note that this choice is made **later**
	- `from sklearn import linear_model`
- (Re-)Seed the `numpy` `default_rng` to calculate our random number generator
- Split the original data into features and target(s)
```python
X = housing_df.drop('target', axis=1)
y = housing_df['target']
```
- Split the features and values into training and test sets
```python
X_train, X_test, y_train, y_test = \
	train_test_split(X, y, test_size=0.2)
```
- Instantiate and fit the model (on the **training** set)
	- Problem: we do not yet know the model/algorithm/estimator we wish to use
	- Use the `sklearn` [machine learning model map](https://scikit-learn.org/stable/machine_learning_map.html)

Using the [machine learning model map](https://scikit-learn.org/stable/machine_learning_map.html)
- Start
- >50 samples **Yes**
- Predicting a category? **No**
- Predicting a quantity? **Yes**
- <100K samples **Yes**
- few features should be important **I am uncertain**
	- So we will **experiment**

We will assume that **all (most) features are important**
- Recommendation from our map: **RidgeRegression**
	- From [Ridge regression](https://scikit-learn.org/1.5/modules/linear_model.html#ridge-regression)
		- "Ridge regression addresses some of the problems of ordinary least squares by imposing a penalty on the size of the coefficients."
```python
model = linear_model.Ridge(alpha=0.5)
model.fit(X_train, y_train)
```

- This algorithm calculates the 
	- Linear coefficients `reg.coef_`
	- Intercept `reg.intercetp_`

We, again, score the model:
- `model.score(X_test, y_test)`

Returns the value of R-squared for the regression
- Value of 0: not predictive at all
- Value of 1: perfectly predictive

How might we improve this model?
- Try out the other models in the [machine learning model map](https://scikit-learn.org/stable/machine_learning_map.html) to improve our model score
