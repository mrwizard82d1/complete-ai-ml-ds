Now that we have prepared our
- Inputs
- Model
- Outputs
- How do we proceed?

Consider reviewing documentation of `tf.keras`
- [The keras documentation](https://www.tensorflow.org/guide/keras/overview)
-  A key question: What is the difference between
	- The sequential
	- And functional API
- Define
	- Input layer
	- Output layers
	- Other layers

We'll create a function that
- Takes the input shape, output shape and model as parameters
- Defines the Keras model **layers** in a sequential fashion
- Compiles the model
- Builds the model
- Returns the model

Create a function that builds a Keras model:
```python
def create_model(
	input_shape=INPUT_SHAPE, 
	output_shape=OUTPUT_SHAPE,
	model_url=MODEL_URL):
	
	print(f'Building model with: {model_url}')

	# Setup the model layers
	model = keras.Sequential([
		# Layer 1
		hub.KerasLayer(model_url, input_shape=input_shape)

		# Layer 2
		keras.layers.Dense(
			units=output_shape, 
			activation='softmax'
		)
	])

	# Compile the model
	model.compile(
		loss=keras.losses.categorical_crossentropy,
		optimizer=keras.optimizers.Adam(),
		metrics=['accuracy'],
	)

	# Build the model
	model.build(input_shape=input_shape)

	# Return the compiled and built model
	return model
```

Now create a model and summarize it
```python
model = create_model()  # Uses our default parameters

model.summary()
```

Hmm... It appears as though the tensor flow API has change (significantly) in the last five years. I will need to investigate these changes to determine how to change my code to conform. Sigh...
