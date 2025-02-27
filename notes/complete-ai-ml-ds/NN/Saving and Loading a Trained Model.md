We've started to evaluate our dog vision model
- An interesting challenge
	- H2 make a confusion matrix
		- Compare's predicted to true
		- See where model is "getting confused"

See the TensorFlow documentation: [Save and load models](https://www.tensorflow.org/tutorials/keras/save_and_load)

Create a function to save a model
```python
def save_model(model, suffix=None):
	"""
	Saves a `model` in a 'models' directory
	"""
	time_stamp = datetime.datetime.isoformat(
		datetime.datetime.now(),
		timespec='seconds'
	)
	model_path = pathlib.Path(
		'models',
		# Video saves model in `hd5` format
		# New recommendation is to save model in 'keras' format
		f'{time_stamp}{"-" + suffix if suffix else ""}.keras'
	)
	print(f'Saving mode to: {model_path}')

	model.save(model_path)
	
	return model_path
```

Let's also create a function to load a model
```python
def load_model(model_path):
	"""
	Loads a saved model stored at `model_path`
	"""
	print(f'Loading model from: {model_path}')
	new_model = keras.model.load_model(
		model_path,
		# Because we have customized our model, we must inform the 
		# loader of our custom layer.
		custom_objects={'KerasLayer': hub.KerasLayer}
	)
	return new_model
```

We now test save and load
```python
saved_model_path = save_model(model, suffix='1000-images-mobilenetv2-Adam)
loaded_1000_image_model = load_model(saved_model_path)
```

We test our saved and (re-)loaded model
```python
model.evaluate(validation_data)
loaded_1000_image_model.evaluate(validation_data)
```

Time to train our model on the **full** dataset
