[Keras Callbacks - Early Stopping](https://www.tensorflow.org/api_docs/python/tf/keras/callbacks/EarlyStopping)

We have a TensorBoard callback that we can monitor

Let's create an early stopping callback
- Helps prevent overfitting
- By stopping the model when an evaluation metric **stops improving**
- Helps prevent **overfitting**

Create our early stopping callback
```python
early_stopping = tf.keras.callbacks.EarlyStopping(
	monitor='val_accuracy',
	patience=3
)
```

We're now ready to 
- Fit our model to the data
- Make a prediction
