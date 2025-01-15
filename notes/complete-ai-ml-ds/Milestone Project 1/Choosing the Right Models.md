Time to start modeling!
- Actually using machine learning-

We're going to try three different machine learning models
	1. Logistic Regression
	2. K-Nearest Neighbors Classifier
	3. Random Forest Classifier

How did we find Logistic Regression?
- Actually, a random search
- But consider the [Scikit-Learn User Model Logistic Regression](https://scikit-learn.org/stable/modules/linear_model.html#logistic-regression)
- Consider this **an experiment**

Because we want to fit and score three different models...
- Let's put our models into a Python `dict`
- Enumerate the items in our dictionary evaluating each candidate
- Using the `toolz` (or `ctools`) packages would probably be very useful here

We write functions to 
- Evaluate a single model (`evaluate_model())
- Evaluate a collection (`dict`) of models (`fit_and_score()`)

Eventually, we'll fit and score all our models in one go for easier comparison
