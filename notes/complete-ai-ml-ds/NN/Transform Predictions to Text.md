A TensorFlow function to ["unbatch" our data](https://www.tensorflow.org/api_docs/python/tf/data/Dataset#unbatch)

Previously talked about how to convert numeric predictions to strings
- We'll now write functions to
	- Convert numbers to strings
	- Visualize the actual image

Even more important than creating a machine learning model is
- **Evaluating** the model
- Remember, too, that our notes are often to ourselves

Since our data is currently **in batches**, we want to "unbatch" the data
- This "unbatch" function allows us to get our
	- Image
	- Our actual label

Remember that TensorFlow provides a function to ["unbatch" our data](https://www.tensorflow.org/api_docs/python/tf/data/Dataset#unbatch)
- Here's code to perform this operation once
```python
images_ = []
labels_ = []

for image, label in validation_data.unbatch().as_numpy_iterator():
	images_.append(image)
	labels_.append(label)

images_[0], labels_[0]
```

Let's turn this cell into a function
- My attempt
```python
# Unroll a data batch  
def unroll_batch(batch):  
    """  
    "Unrolls" a `DataBatch` into each item in the batch.  
    :param batch: The batch to unroll.
	:return: A list of batch items.  
    """
    return [(image_, label_) 
		    for (image_, label_) in 
		    validation_data.unbatch().as_numpy_iterator()]
```
- And Daniel's function
```python
# Create a function to "unbatch" a batch dataset.  
def unbatchify(data):  
    """  
    Takes a batched `DataSet` of (image, label) Tensors and returns    separate arrays of images and values.
    :param data: The batch `DataSet`.
    :return: The unrolled batch.  
    """  
    images_ = []  
    labels = []  
  
    # Loop through unbatched data  
    for image_, label_ in data:  
        images_.append(image_)  
        labels.append(label_)  
  
    return images_, labels_
```
- These two function return the same results for the two test cases:
	- Item 0
	- Item 42
- I thought the returned different results at first, but I verified that they seem to return the same values

But I'll use Daniel's function in the future to avoid issues
- We'll make functions 
	- To visualize an image
	- To compare the truth label to the predicted label
