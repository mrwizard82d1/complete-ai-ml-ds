We are on the home stretch
- About to save and load our model

Once we are happy to share our model, what do we do?
- Export model to file
- Share with other interested parties

Two ways to save and load machine learning models
1. Using Python's `pickle` module
2. Using the `joblib` module

We'll start with saving a model using `pickle`
```python
import pickle

with open('gs_random_forest_model_1.pkl', 
		  'wb') as f:
	pickle.dump(gs_classifier, f)
```
- One may want to save models to a `models` directory

Loading a model using `pickle`
```python
import pickle

with open(
	'gs_random_forest_model_1.pkl', 'rb'
) as f:
	loaded_pickle_model = pickle.load(f)
```

In the next video, we'll see how to perform the same steps using `joblib`
