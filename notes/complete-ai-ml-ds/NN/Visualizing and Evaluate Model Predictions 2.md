We have one function to visualize
- What other predictions can our model make?

Let's make a function to view the "top 10" predictions of our model
- This function will
	- Take inputs of
		- Prediction probabilities array
		- Ground truth array
		- An integer (identifying a...)
	- Find the prediction using `get_prediction_label()`
	- Find the top 10
		- Prediction probabilities indices
		- Prediction probabilities values
		- Prediction labels
	- Plot the top 10 prediction probability values and labels
		- Coloring the true label green

We did some prototyping of our function

And then we wrote our function
```python
def plot_prediction_confidence(
	prediction_probabilities,
	truth_labels,
	n=1
):
	prediction_probability = prediction_probabilities[n]
	truth_label = truth_labels[n]

	# Seemingly unnecessary
	prediction_label = get_prediction_label(prediction_probability)

	top_10_prediction_indices = \
		prediction_probability.argsort()[-10:][::-1]

	top_10_prediction_values = \
		prediction_probability[top_10_prediction_indices]

	top_10_prediction_labels = unique_breeds[top_10_prediction_indices]

	top_plt = plt.bar(
		np.arange(len(top_10_prediction_labels)),
		top_10_prediction_values,
		color='grey'
	)

	# Colors instead numbers across the bottom of the plot 
	plt.xticks(
		np.arange(len(top_10_prediction_labels)),
		labels=top_10_prediction_labels,
		rotation='vertical',
	)

	# Change the color of the true label to green
	if np.isin(truth_label, top_10_prediction_labes):
		top_plot[
			np.argmax(top_10_prediction_values == truth_label)
		].set_color('green')
	else:
		pass
```

And then we plot it:
```python
plot_prediction_confidence(
	prediction_probabilities=predictions,
	truth_labels=validation_labels,
	n=9,
)
```
- The result: a collie

In the next video, we'll write some code to combine
- `plot_predictions()`
- `plot_predictions_confidence()`
- We'll plot the
	- Image on the left
	- The image confidences on the right
	- Perhaps for 10 images or so
- But we'll write this code in the next video
