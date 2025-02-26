We've made our models "more visual"
- Critical in communicating to others
- Additionally, how will we integrate models with other functions

Let's write code to visualize more than one 
- We want both
	- An image
	- Its confidences compared to other images

Here's our code
```python
# Also test multiplier of 10 and 20
i_multiplier = 0
num_rows = 3
num_cols = 2
num_images = num_rows * num_cols

plt.figure(figsize=(10 * num_cols, 5 * num_rows))

for i in range(num_images):
	# Plot image under test
	plt.subplot(num_rows, 2 * num_cols, 2 * i + 1)
	plt.predictions(
		prediction_probabilities=predictions,
		truth_labels=validation_labels,
		images=validation_images,
		n=i + i_multiplier
	)

	# Plot image confidences
	plt.subplot(num_rows, 2 * num_cols, 2 * i + 2)
	plot_prediction_confidence(
		prediction_probabilities=predictions,
		truth_labels=validation_labels,
		n=i + i_multiplier
	)

plt.tight_layout(h_pad=1.0)
plt.show()
```

Let's see how to save and restore our trained model in TensorFlow
- In the next video
