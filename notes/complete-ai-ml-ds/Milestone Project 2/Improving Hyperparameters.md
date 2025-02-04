We used `RandomizedSearchCV` to help tune our hyperparameters
- But only a small number of iterations
	- Daniel performed two iterations
	- I performed six

Daniel found the following "ideal" hyperparameters in a six-hour experiment
```python
{
	'Training MAE': 6633.714300615716,
	'Valid MAE': 8074.634589086979,
	'Training RMSLE': 0.2967133662928448,
	'Valid RMSLE': 0.32142476459239144,
	'Training R^2': 0.807156908286598,
	'Valid R^2': 0.7827628271827418,
}
```

We'll now train our model with the "best" hyperparameters (found by Daniel)
```python
%%time

ideal_model = RandomForestRegressor {
	n_jobs=-1,
	random_state=42,
	n_estimators=40,
	min_samples_leaf=1,
	min_samples_split=14,
	max_features=0.5,
	max_samples=None
}

ideal_model.fit(X_train, y_train)
```
- And now we score the model (and compare it our scores for `rs_model`)
```python
show_scores(ideal_mode)
show_scares(rs_model)
```
- I see no difference in the scores
	- Daniel sees a reduction in RMSLE
	- In top 30 of Kaggle leader board

If we were to submit to Kaggle, we need to submit a submission file
- Tune into the next video
