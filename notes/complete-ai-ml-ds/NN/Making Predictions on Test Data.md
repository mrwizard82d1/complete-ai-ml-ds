We now have a model trained on the full data set
- 10,000 images and labels

We'll now make some predictions on our test data
- Also about 10,000 images and labels

Making predictions on the test data set
- Before making predictions,
	- We must convert our test data to numbers in tensor batches

At this point in our data science "careers"
- Two key items of focus are
	- The inputs
	- The outputs
- We will eventually be able to spend more time on our machine learning algorithm

Load our test image path names
```python
test_dir_path_name = pathlib.Path()'./data/test/')
test_path_names = [
	path_name for path_name in test_dir_path_names.iterdir()
]
```
- We now have all our path names

Convert the path names into test data batches using `create_data_batches()`
```python
test_data = create_data_batches(
	[str(test_path_name) for test_path_name in test_path_names],
	test_data=True
)
```

Now, the finale: make a predictions array
```python
test_predictions = loaded_full_model.predict(
	test_data,
	verbose=1,
)
```

In the next video, we will convert our data to the format expected by Kaggle
