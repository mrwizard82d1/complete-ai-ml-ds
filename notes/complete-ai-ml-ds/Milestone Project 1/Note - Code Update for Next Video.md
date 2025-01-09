Some updates as of `scikit-learn` version 1.2+
- `plot_roc_curve` is now `RocCurveDisplay`

Previous code that will throw an error:
```python
from sklearn.metrics import plot_roc_curve
```

New code (after `scikit-learn` 1.2+)
```python
from sklearn.metrics import RocCurveDisplay
```

A reminder on checking the version of `sklearn`
```python
import sklearn
sklearn.__version__
```

If you want to update your version of `scikit-learn`:
```bash
conda update -n heart-disease-project scikit-learn
```
