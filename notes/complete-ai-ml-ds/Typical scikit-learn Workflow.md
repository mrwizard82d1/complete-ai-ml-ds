Set up project
- `conda env list` - list `conda` environments
- `conda activate complete-ai-ml-ds`
- `jupyter lab`

Create a new notebook
- `introduction-to-scikit-learn.ipynb`

What we're going to cover:
0. An end-to-end Scikit-Learn workflow
1. Getting the data ready
2. Choose the right estimator (model) / algorithm for our problems
3. Fit the model / algorithm and use it to make predictions on our data
4. Evaluating a model
5. Improve a model
6. Save and load a trained model
7. Putting it all together

Get the data ready
- Read the `.csv` file 
	- `heart_disease = pd.read_csv('./data/heart-disease.csv')`

Our goal
- Use the different columns of data in `heart_disease` 
- To predict the `target` column (does or does not have heart disease)

First things first: get the data ready
- We need a "feature matrix"
	- AKA data, feature variables
	- Typically called `X`
	- `X = heart_disease.drop('target', axis=1)`
		- Remember 
			- `axis=0` for **rows**
			- `axis=1` for **columns**
- We need our "label"	
	- Typically called `y` (notice the case difference `X` and `y`)
	- AKA "label matrix"
	- `y = heart_disease['target']` 

Step 2: Choose the right estimator for our problems
- Our problem is classification
- We need to choose the right
	- Model
	- Hyperparameters - like "dials" we can use to "tune" our model
- Let's use a "random forest"
	- Why!?
	- See the Wikipedia article on [Random forest](https://en.wikipedia.org/wiki/Random_forest) for basic information about the algorithm
	- `from sklearn.ensemble import RandomForestClassifier`
		- A classification machine learning model
	- `clf` - a typical TLA for a "classifier"
	- Use the default hyperparameters
		- `clf.get_params()`

Step 3: Fit the model to the training data
- Split the data into training and testing split(s)
	- `from sklearn.model_selection import train_test_split`
- Split into
	- `X_train`
	- `X_test`
	- `y_train`
	- `y_test`
- Add optional parameter, `test_size=0.2`
	- Reserve 20% of the data for testing
- Fit our training data
	- `clf.fit(X_train, y_train)`
- Make a prediction
	- `y_label = clf.predict(X_test)`

Step 4: Evaluate the model on both training and test data
- `clf.score(X_train, y_train)`
- `clf.score(X_test, y_test)`
- The function, `clf.score()`
	- "Returns the mean accuracy on the given test data and labels." (from the documentation)
- Getting 100% on the training data is not surprising
- Getting 100% on the test data might cause us to think we have a problem
- Other evaluation "metrics" are:
	- `classification_report`
		- [Understanding a Classification Report](https://medium.com/@kohlishivam5522/understanding-a-classification-report-for-your-machine-learning-model-88815e2ce397)
	- `confusion_matrix`
		- AKA "error matrix"
		- In unsupervised learning, usually called a "matching matrix"
		- See the Wikipedia article, [Confusion matrix](https://en.wikipedia.org/wiki/Confusion_matrix)
		- This table allows a more detailed analysis than simply observing the proportion of correct classifications (accuracy)
	- `accuracy_score`
		- See the Wikipedia article, [Precision and recall](https://en.wikipedia.org/wiki/Precision_and_recall)
			- **Lots** of detail

Step 5: Improve a model
- For example
	- Try different amounts of `n_estimators`
	- Calculate a well-known random number generator
		- This allows our notebook to be reproducible
	- Print results of different `n_estimators`
	- Loop through different estimators in `range(10, 100, 10)`
	- Our most accurate (after much wailing and gnashing of teeth) occurred with **50** estimators

Step 6: Save and load a trained model
- Prerequisite: `import pickle`
- Save the model

```python
with open('./random_forest_model_1.pkl', 'wb') as f:
	pickle.dump(clf, f)
```

- Load the model

```python
with open('./random_forest_model_1.pkl', 'rb') as f:
	loaded_model = pickle.load(f)

loaded_model.score(X_test, y_test)
```

We have now (quickly) gone through all our steps