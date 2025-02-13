We have been getting our data into an accessible format
- Now we want to create our own validation set
	- Since it is not provided to us

Remember the most important concept in machine learning
- Train on the training set
- Evaluate on the validation set to check experiments
- The "final exam" is the test set

We have a training set and a test set
- But **no** validation set

How do we split our data
```python
# Split data into features (`X`) and labels (`y`)
X = path_names
y = boolean_labels
```

We have ~ 10k examples
- This will **take time**
- Because we want to experiment quickly
	- We will start by experimenting with ~ 1k images
	- We increase the amount as necessary

Set number of images to use for experimenting
```python
# A common convention is that variables in all caps 
# are **hyperparameters**
NUM_IMAGES = 1000

# Google Colab allows one to "attach" a UI widget, for example, a slider,
# to this variable for easier changing of the value
```

Let's split our data into
- Training and
- Validation sets
- The validation set will have a size of `NUM_IMAGES`
```python
from sklearn.model_selection import train_test_split

X_train, X_validation, y_train, y_validation = train_test_split(
	X[:NUM_IMAGES],
	y[:NUM_IMAGES],
	test_size=0.2,
	random_state=42,
)
```

Be sure to check the sizes
- It is **far too easy** to create splits of the **wrong** size
- And then **waste time** on issues caused by the wrong sized splits

We now have a small training and validation set
- We are now ready to **turn our data into tensors**
