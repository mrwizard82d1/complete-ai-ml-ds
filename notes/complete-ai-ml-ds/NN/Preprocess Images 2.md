We've now seen what an image looks like as a tensor.
- Let's make a function to preprocess them.

Our function outline
- Take an image path name as input  
- Use TensorFlow to read the file and save it to a variable, for  
example, `image`  
- Turn our `image` (a jgp) into Tensors 
- Normalize our image; that is, convert the color channel values from the integer range (0, 255) to the floating point range (0, 1)
- Resize the `image` to have a shape of (224, 224)  
- Return the modified `image`

Our code
```python
IMAGE_SIZE = 224

def preprocess_image(image_pathname):
	# Read the image
	image = tf.io.read_file(image_pathname)

	# Turn the jpeg image into a tensor with 3 color (RGB) channels
	image = tg.image.decode_jpeg(image, channels=3)

	# Convert the color values from range (0, 255) to range (0, 1)
	# In other words, normalize our image)
	image = tf.image_convert_image_dtype(image, tf.float32)
```

An aside
- If you ever see a function that you **do not understand**
	- Rewrite the function in a notebook line-by-line

When we read through the TensorFlow documentation on loading data, we will note that
- TensorFlow likes to read data in batches. So...
- We need to determine how to read our data in batches
