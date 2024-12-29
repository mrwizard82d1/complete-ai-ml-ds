We've now figured out how to evaluate machine learning models
- We'll now learn how to improve our model(s)

Terminology:
- First predictions == baseline predictions
- First model == baseline model

From a data perspective
- Could we **collect** more data?
	- In general, the more data the better
- Could we **improve** our data?

From a model perspective
- Is there a better model we could use?
	- [Local machine learning model map](./ml_map.svg)
	- [Online machine learning model map](https://scikit-learn.org/stable/machine_learning_map.html)
- Could we **improve** the current model?

General improvements of models
- Use a simple model
	- For example, Linear SVC
- Alternative, use an ensemble model

Two different "levers" to improve models
- Parameters 
	- Models find these patterns in data
- Hyperparameters 
	- Settings on a model that one can adjust to (potentially) improve its ability to find (better) patterns

But how do you discover a models hyperparameters?
- Calling the function `clf.get_parames()`
- Returns a list of candidate hyperparameters

H2 discover hyperparameters?
- Search the `sklearn` documentation on `RandomForestClassifier`
- Note that the `sklearn`  documentation calls "hyperparameters" **parameters**

Hyperparameter tuning
- Like adjusting the temperature of the oven in a recipe
![[Hyperparameter tuning analogy.png]]
Three ways to adjust hyperparameters
1. By hand
2. Randomly with `RandomSearchCV`
	- A function in `scikit-learn`
3. Exhaustively with `GridSearchCV`
	- Another function in `scikit-learn`
