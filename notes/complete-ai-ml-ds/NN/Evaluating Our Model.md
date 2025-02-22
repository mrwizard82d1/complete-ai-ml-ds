[Keras Callbacks](https://www.tensorflow.org/api_docs/python/tf/keras/callbacks/TensorBoard)

Our model is ready to go and we understand summarizing our model
- Let's make some callbacks

What are callbacks?
- Helper functions a model can use during training to do tasks like:
	- Save its progress
	- Check its progress
	- Stop training early if a model stops improving
- Help us answer the question: "What is happening?"

Let's create a couple of callbacks
- One for TensorBoard which helps track the progress of our model
- Another for early stopping which prevents our model from training too long

To setup a TensorBoard callback, we must do three things:
1. Load the TensorBoard notebook extension
2. Create a TensorBoard callback which is able to save longs to a directory and pass it to our model's `fit()` function
3. Visualize our model's training logs with the `%tensorboard` magic function
	- We'll perform this visualization **after** model training

We'll be storing logs locally so we create a `logs` directory

We write function to build a TensorBoard callback
```python
def create_tensorboard_callback():
	# Create a log directory for storing TensorBoard logs
	log_dir = pathlib.Path(
		'.',
		'logs',
		datetime.datetime.now().isoformat(timespec='seconds')
	)
	return tf.keras.callbacks.TensorBoard(log_dir=log_dir)
```
