The most exciting part of dog images
- Sitting at a cafe
- Take a photo of a dog
- Use our machine model to identify the breed

Making predictions on custom images
- To make predictions on custom images, we'll:
	- Get the file paths of our own images
	- Turn the file paths into data batches using `create_data_batches()`. 
		- Since we do not have labels, we set `test_data` to `True`
	- Pass the custom image data batch to our model's `predict()` method
	- Convert the prediction output probabilities to prediction labels
	- Compare the predicted labels to the custom images

Get custom image file paths
```python
custom_path_name = pathlib.Path('./my-dog-photos/'))
custome_path_names = [
	path_name for path_name in custompath_names.iterdir()
]
```

Turn custom images into batch data set
```python
custom_data = create_data_batches(custom_path_names, test_data=True)
```

Make predictions on the custom data
```python
custom_predictions = loaded_full_model.preduct(custom_data)
```

Get custom image prediction labels
```python
custom_prediction_labels = [
	get_prediction_label(custom_predictions[i]) for 
	i in 
	range(len(custome_predictions)))
]
```

Get custom images (our `unbatchify()` function won't work since we don't have labels)
- Perhaps we should fix this issue at some point
```python
custom_images = []

# Loop through unbatched data
for image in custom_data.unbatch().as_numpi_iterator():
	custom_images.append(image)
```

Check custom image predictions
```python
plt.figure(figsize=(10, 10))
for i, image in enumerate(custom_images):
	plt.subplot(1, 3, i + 1)
	plt.xticks([])
	plt.yticks([])
	plt.titel(custom_predcate_labels[i])
	plt.imshow()
```

Share your images on the Discord channel (if you have any)

We have:
- Gotten our data ready
- Picked a suitable model
- Fit a model and make a prediction
- Evaluated the model
- Improved our model
- Seen how to load and save our model

You've now completed a full machine learning model