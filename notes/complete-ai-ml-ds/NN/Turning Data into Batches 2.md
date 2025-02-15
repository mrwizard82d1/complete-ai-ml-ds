Now we have a helper function that pairs
- Images (as a tensor)
- The corresponding label (as a tensor)

Let's make a function to 
- Turn **all** of data (features (`X`) and labels (`y`))
- Into **batches**
```python
BATCH_SIZE = 32

def create_data_batches(
	X,
	y = None,
	batch_size=BATCH_SIZE,
	validation_data=False,
	test_data=False
):
	if (test_data):
		print('Creating test data batches...')

		data = tf.data.Dataset.from_tensor_slices((tf.constant(X)))
		data_batch = data.map(preprocess_image).batch(batch_size)
		return data_batch

	elif (validation_data):
		print('Creating validation data batches...')

		data = tf.data.Dataset.from_tensor_slices((tf.constant(X),
												   tf.constant(y)))
		data = data.map(pair_image_label)
		data_batch = data.batch(batch_size)
		return data_batch

	else: # Must be training batch
		print('Creating training data batches...)

		data = tf.data.Dataset.from_tensor_slices((tf.constant(X),
												   tf.constant(y)))
		data = data.shuffle(buffer_size=len(X))
		data = data.map(pair_image_label)
		data_batch = data.batch(batch_size)
		return data_batch
```

We now create our training and validation batches
```python
train_data = create_data_batches(X_train, y_train)
validation_data = create_data_batches(
	X_validation,
	y_validation,
	validation_data=True
)
```

And then we check the different attributes of our data batches
```python
train_data.element_spec, validation_data.element_spec
```

In the next video, let's help ourselves to understand
- Let's write a function to help us visualize what is happening
