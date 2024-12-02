Prerequisites:
- What to cover:
	0. An end-to-end Scikit-Learn workflow
	1. Getting the data ready
	2. Choose the right estimator/algorithm/model for your problem
	3. Fitting your chosen machine learning model to the data and using it to make a prediction
	4. Evaluating a machine learning model
	5. Improving predictions through experimentation (hyperparameter tuning)
	6. Saving and loading a pre-trained model
	7. Putting it altogether in a pipeline
- "Standard imports"
```python
import pandas as pd
import numpy as nmp
import matplotlib.pyplot as plt
```

Getting our data ready to be used with machine learning
- Three main steps
	1. Split the data into features and labels (usually `X` and `y`)
	2. Filling (AKA "imputing") or disregarding missing values
	3. Converting non-numerical values to numerical values (also called "feature encoding")

Split our data into "features" and "labels" (`X` and `y`)
- Use the already imported `heart_disease`
- Our features are all the columns **but** `target`
	- `X = heart_disease.drop('target', axis=1)`
- Our labels are **only** the `target` column
	- `y = heart_disease['target']`

Split our features and labels into training and test sets
- Reserve 20% of our data for testing
```python
from sklearn.model import train_test_split
(X_train, X_test, y_train, y_test) = train_test_split(X, y, test_size=0.2)
```

Our next step: filling (imputing) or disregarding missing data
