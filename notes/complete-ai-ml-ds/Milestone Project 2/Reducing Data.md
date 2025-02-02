Now that we have a custom validation function, we can train and test
- But not so fast...

Testing our value on a subset (to tune the hyperparameters)
- Testing on the entire model took over 5 minutes in the video
- Only took a little over 1 minute on my system
- Do not want to take 5 minutes to perform testing
	- Our solution: run our model on a **subset** of our training
	- We could just simply fit a **subset** of our data but...
	- We could change the `max_samples` values

Change our model to use fewer samples for training / tuning
```python
model = RandomForestRegressor(
	n_jobs=-1,
	random_state=42,
	max_samples=10_000,
)
```
- And then we can time and train our model
```python
%%time
model.fit(X_train, y_train)
```
- Finally, we can show our scores
```python
show_scores(model)
```

Now that we've determined how to train our model a bit quickly
- We may want to improve our hyperparameters
