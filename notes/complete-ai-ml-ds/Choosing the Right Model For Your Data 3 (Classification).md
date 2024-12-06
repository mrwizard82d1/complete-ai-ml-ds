We've seen how to choose an estimator for a regression problem
- How do choose an estimator for a classification problem?

We will use the "heart-disease" data frame

Our first step:
- Use the [Online machine learning model map](https://scikit-learn.org/stable/machine_learning_map.html)
- Start
- > 50 samples? **Yes**
- Predicting a category? **Yes**
- Do you have **labeled data**? **Yes**
- < 100k samples? **Yes**
- Try "Linear SVC"

Scikit-Learn documentation
- SVC, NuSVC, and LinearSVC are
	- Classes
	- Capable of performing
		- Binary and
		- Multi-class classification
		- On a dataset

What is "Linear SVC"?
- Linear Support Vector Classification
- Similar to SVM
- Different implementation (`liblinear`)
- Has more flexibility in the choice of
	- Penalties
	- Loss functions
- Should scale better to **large numbers of samples**

We again adopt our typical steps
- Import (the classifier)
```python
from sklearn.svm import LinearSVC
```
- Initialize a repeatable random number generator
```python
rng = np.random.default_rng (
	4577550920016562965326478789717866486
)
```
- Split the data into features and values (`X` and `y`)
```python
X = heart_disease.drop('target', axis=1)
y = heart_disease['target']
```
- Further split the data into testing and training splits
```python
X_train, X_test, y_train, y_test = \
	train_test_split(X, y, test_size=0.2)
```
- Instantiate our model
```python
clf = LinearSVC() # `clf` is a TLA for "classifier"
clf.fit(X_train, y_train)
clf.score(X_test, y_test)
```

Executing this code in the video generates a warning
- "ConvergenceWarning: Liblinear failed to converge, increase the number of iterations."
- In version 1.5 of `sklearn`, I see **no such warning**

The score in the video and my score differ **significantly**
- Video score: 0.475
- Score from `sklearn` 1.5: 0.770
- Since 
	- The score **in the video** is only 0.475
	- The number of classes found is only **two**
	- We should check **other** candidate classification algorithms
	- I hope another algorithm might even improve my 0.770 score.

What alternatives might we employ to `LinearSVC`?
- Do we have text data? **No**
- Try a K-neighbors classifier!
- However, Daniel has chosen to skip that.
- I, however, will try it out
	- Hmm... I read the docs for
		- `NearestNeighbors`
		- `KDTree`
		- `BallTree` 
	- However, I was unclear how to relate the documented usage with what I have previously seen so...
- Back to the video

On to ensemble classifiers
- Remember, when we previously switched to `RandomForestRegressor`, we saw an **increase** in our score
- Hopefully, `RandomForestClassifier`, will have similar results

An interesting note from the [documentation](https://scikit-learn.org/stable/modules/ensemble.html#random-forests):

> The purpose of these two sources of randomness is to decrease the variance of the forest estimator. Indeed, individual decision trees typically exhibit high variance and tend to overfit. The injected randomness in forests yield decision trees with somewhat decoupled prediction errors. By taking an average of those predictions, some errors can cancel out. Random forests achieve a reduced variance by combining diverse trees, sometimes at the cost of a slight increase in bias. In practice the variance reduction is often significant hence yielding an overall better model.

To save time, we will **copy** the `LinearSVC` code we've already used
- Change import
```python
from sklearn.ensembles import RandomForestClassifier
```
- The result: 0.836!

Notice that our ensemble methods in both 
- Regression
- Classification
- **Improved** our scores
- One could actually have tried all the models in our map
- However, a machine learning tidbit from Daniel
> If you have structured data - AKA tables or data frames - use ensemble methods. Why? Because it will perform pretty well.

> If there are patterns...

A machine learning tidbit:

| If you have...    | Then use...                                        |
| ----------------- | -------------------------------------------------- |
| Structured data   | Ensemble methods                                   |
| Unstructured data | Deep learning methods or transfer learning methods |

Data examples

| Structured Data                          | Unstructured Data             |
| ---------------------------------------- | ----------------------------- |
| Data in a table like our `heart_disease` | - Images<br>- Audio<br>- Text |
Remember, a critical success factor in data science is
- **Reducing** your time between experiments

Our next sections
- Fitting a model to data
- Making predictions with our model
