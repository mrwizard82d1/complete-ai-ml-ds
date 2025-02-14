We have split our data into 
- Training and
- Verification splits

Our labels have already been converted to numbers.
- How do we convert our data (images) into numbers (specifically, Tensors)?

Remember our theme
- Create functions that we can write code once
- And apply it to different instances of the same data

To preprocess our images into Tensors, we write a function that:

- Takes an image path name as input
- Uses TensorFlow to read the file and save it to a variable, for example, `image`
- Turns our `image` (a jpg) into Tensors
- Resize the `image` to have a shape of (224, 224)
- Return the modified `image`

But... Before we write this function, let's investigate how to import an image
```python
# Convert an image to a `numpy.array`
from matplotlib.pyplot import imread

image = imread(path_names[42])
image.shape

# Believe the `shape` tuple is (height, width, color_channel)
```

We now have our image data stored in a `numpy.array`
- H2 create a Tensor?
- `tf.constant()` will convert almost any data structure into a Tensor
- Once we've converted our image into a tensor,
	- We can run our calculations on the GPU
		- **Much faster** than using our CPU

Finally, let's write our function
- But... in the next video
