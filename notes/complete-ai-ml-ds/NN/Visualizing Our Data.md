We now have our data in batches
- But batches can be hard to understand
- Let's visualize them!

Here's our code to plot batched images.
```python
def show_25_images(images, labels):
	plt.figure(figsize=(10, 10))

	for i in range(25):
		ax = plt.subplot(5, 5, i + 1)
		plt.imshow(images[i])
		plt.title(unique_breeds[labels[i].argmax()])
		plt.axis('off')
```

To actually visualize our images, we must "unbatch" our batches
```python
train_images, train_labels = next(train_data.as_numpy_iterator)
```

Now we'll visualize the data in a training batch
```python
show_25_images(train_images, train_labels)
```

If we want to visualize other batches
```python
train_images, train_labels = next(train_data.as_numpy_iterator)
show_25_images(train_images, train_labels)
```

Now that we've visualized our batches
- Let's build and train our model!
- In the next video
