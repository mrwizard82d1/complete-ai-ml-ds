HWe've seen how to choose a learning model
- Now we're ready to use a fitted model to **make predictions**

We'll copy some of our previous code to help us out
```python
from sklearn.ensemble import RandomForestClassifier
```

```python
import[[ ]]secrets  
  
seed = secrets.randbits(123)  
seed
```

```python
rng = np.random.default_rng(seed=2075748097716160523040509094081475903)
```
```python
X = heart_disease.drop('target', axis=1)  
y = heart_disease['target']  
  
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2)  
  
clf = RandomForestClassifier()
clf.fit(X_train, y_train)  
clf.score(X_test, y_test)
```

Our main concern: the **fit**
- What is `fit` **actually doing**?
	- Loop through all our **training data**
	- Try to determine what **patterns** of **data** produce similar **values**
- How this works, in detail, would require (too) much time
	- Similar to how you as a person might try to determine which **variables** best "predict" the expected **data**

In production,
- We use the **created model** to make "actual" predictions (results)

The **crux** of machine learning
- Finding **patterns** in **data** that allow us to **predict** the **value** of interest

Onto making predictions with our model
