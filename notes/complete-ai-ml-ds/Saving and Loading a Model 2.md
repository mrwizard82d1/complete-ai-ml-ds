We saw how to save and load a model using `pickle`
- Now we'll use `joblib`

Saving a model using `joblib`
```python
from joblib import (dump, load)

dump(
	 gs_classifier, 
	 filename=\ 'models/gs_random_forest_model_1.joblib'
)
```

Loading a model using `joblib`
```python
from joblib import (dump, load)

loaded_joblib_model = \ 
	load(filanem='models/gs_random_forest_model_1.joblib')
```

Which serialization package should you use?
- `pickle` or `joblib`?
- See the [scikit-learn documentation on model persistence](https://scikit-learn.org/stable/model_persistence.html) for
	- Storage options (more than in video)
	- When to use each option

Next, we'll see how to "put it all together"
