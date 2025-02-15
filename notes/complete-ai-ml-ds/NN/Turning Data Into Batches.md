We've written a function to turn our data into tensors
- Next step: pick a model
- But we're not quite ready to pick a model

So we'll learn more about loading data into TensorFlow
- Specifically, reading data into a batch
	- AKA, a mini-batch
	- 32 is an appropriate number
	- Why
		- Search "yann lecun batch size"
		- Or "jeremy howard batch size"
	- We'll use "yann lecun" because his work on image processing
		- From Twitter
			- "Friends don't let friends use minibatches larger than 32."

Why turn our data into batches?
- If we try to process >~ 10k images at one time
	- They may not fit into memory
	- Consequently, the OS will swap our data to and from disk as it tries to process these images
	- **Very, very** slow (at least 1000 times slower than in-memory)
- Consequently, we process
	- About 32 (the "batch size") images at a time
	- You can manually adjust the batch size if necessary

In order to use TensorFlow effectively, we need our data
- In the form of a "tensor tuple"
- That is, in the tuple, `(image, label)`

Create a simple function to return a tuple, `(image, label)`
```python
def pair_image_label_tuple(image_path, label):
	image = preprocess_image(image_path)
	return image, tf.consant(label)
```
In the next video, we will turn our data into batches
- Differs depending on
	- Training batch
	- Validation batch
	- Test batch
- We'll see this work in the next video
