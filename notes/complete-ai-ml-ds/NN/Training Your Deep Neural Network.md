We've come a long way
- But we're ready to train our first deep learning model (on a subset of data)

Training a model (on a subset of data)
- We train on a subset to avoid 
	- Committing large amounts of time
	- On **failures**

We must define one additional variable before training our model
- The number of "epochs"
- An "epoch" is
	- A **single** pass through our data

One last check to ensure we're using a GPU
- Because using a GPU so significantly saves us time
```python
print(
	'GPU',
	'available (YESSS!!!)' if tf.config.list_physical_devices('GPU')
	else 'not available :('
)
```

Let's create a simple function that trains a model
- Here are the "steps"
	- Create a model using `create_model()`
	- Setup a TensorBoard callback using `create_tensorboard_callback()`
	- Call the `fit()` function on our model passing
		- The training data
		- The validation data
		- The number of epochs for training (`NUM_EPOCHS`)
		- The callbacks we wish to use
	- Return the model

Here's the code:
```python
def train_model()
	model = create_model()

	tensorboard = create_tensorboard_callback()

	model.fit(
		x=train_data,
		epochs=NUM_EPOCHS,
		validation_data=validation_data,
		validation_freq=1, # Validate at every epoch
		callbacks=[tensorboard, early_stopping],
	)

	return model
```

Rule of thumb
- When training data for the first time, the first epoch will usually take longer than the rest
	- Must load data into GPU memory
- Subsequent epochs tend to be faster

Observations
- First epoch took time
- Faster on remaining epochs
- Early stopping stopped at run 12/100
	- loss 0.310
	- accuracy 1.0000
	- val_loss: 1.3672
	- val_accuracy: 0.6500

**Question**
- It looks like our model is overfitting because it is performing far better:
	- On the training dataset
	- Than on the validation dataset
- What are some ways to prevent model overfitting in deep learning neural networks?

**Note**:
- Overfitting to begin with is a **good thing**
- It means that our model is **learning**

Our next steps
- Evaluate the model
- Make a prediction
