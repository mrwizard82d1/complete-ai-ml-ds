Now its time to train our model on **all** the data
- Our smaller model seems to be working
- Let's try the "whole enchilada"

Remember our workflow
1. Get data ready (turn into tensors) - `create_data_batches()`
2. Pick a model - `create_model()`
3. Fit model to data and make predictions

Let's "give it a crack"
- This repetition is where functions really help
- `full_data = create_data_batches(X, y)`
- `full_model = create_model()`

We need to create full model callbacks
```python
full_model_tensorboard = create_tensorboard_callback()
```
- Remember, we have **no** validation set when training the full model
	- Consequently, we **cannot** monitor validation accuracy
```python
full_model_early_stopping = \
	tf.keras.callbacks.EarlyStopping(
		monitor='accuracy',
		patience=3,
	)
```

Remember, fitting the whole model **make take time**
- The GPU must load all the images into memory
- Because training entire models takes **significant time**
	- It is critical to perform some early work to
		- Lessen the likelihood that our training fails 
		- When testing all our data
```python
full_model.fit(
	X=full_data,
	epochs = NUM_EPOCHS,
	callbacks=[
		full_model_tensorboard,
		full_model_early_stopping,
	],
)
```

Let's examine our training
- Real models **take time**

Critical first step when training completes
- **Save our model**
```python
save_model(full_model, suffix='full-image-set-mobilenetv2-Adam')
```

Numbers look good...
- loss = 0.0119
- accuracy = 0.9987
- But since we've not validated, take results with a "grain of salt"

Load our saved model
```python
loaded_full_model = \
	load_model('models/2025-02-27T17:39:59-full-image-set-mobilenetv2-Adam.keras')
```

What's next?
- Let's make some predictions on the test data set
- In the next video
