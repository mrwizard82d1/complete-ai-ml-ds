We now have a way to get
- Validation images
- Validation labels
- Prediction labels

Now we'll visualize things
- Prediction labels
- Validation labels ("the truth")
- Validation images
- This step helps us to communicate better to others
- By creating functions to support visualization, we can communicate our findings more easily

Let's create a function that:

- Accepts
	- An array of prediction probabilities
	- An array of truth labels
	- An array of images
	- An array of integers
- Converts
	- The prediction probabilities to a predicted label
- Plots, on a single plot,
	- The predicted label
	- Its predicted probability
	- The truth label
	- The target image

Here's the function definition
```python
def plot_predictions(
	prediction_probabilities,
	truth_labels,
	images,
	n=1
):
	prediction_probability = prediction_probabilities[n]
	truth_label = truth_labels[n]
	image = images[n]

	prediction_label = get_prediction_label(prediction_probability)

	plt.imshow(image)

	# Clear ticks from both axes
	plt.xticks([])
	plt.yticks([])

	plt.title(
		f'{prediction_label} ' +
		f'{np.max(prediction_probabilities) * 100:2.0f} ' + 
		f'{truth_label}'
	)
```

And then we plot our predictions
```python
plot_predictions(
	prediction_probabilities=predictions,
	truth_labels=validation_labels,
	imags=validation_images
)
```

When we test breed indices:
- 0, 1, 42, 77
- We score 50%

Interesting to know
- What other breeds our machine thought it might be
- In the next video, we'll show the "top ten" predictions
