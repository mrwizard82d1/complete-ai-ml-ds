Now that our data in in tensor batches
- We can return to our workflow
- We've completed step 1
	- Has taken much time, but not terribly unexpected
	- We want our input to be useful to a machine learning algorithm
- Our next step
	- Pick a model from TensorFlow Hub to suit our problem
	- Key: **algorithm already implemented**

Remember that 
- Deep learning supports many different success paths and 
- Building a model is **expensive**

To address some of these issues we use **transfer learning**
- We begin with a pre-built model
- If necessary, we will further refine that model
- This approach saves us
	- Energy
	- Cost
	- Time (we can get "up and running" more quickly than "starting from scratch")

Building a model
- We must define
	- Our input shape to our model
	- The output shape from our model
	- The URL of the model (machine learning algorithm) we want to use

Setup the "shapes" for our problem
```python
# The input shape of our model
# - Batch (`None`)
# - Image height (`IMAGE_SIZE`)
# - Image width (`IMAGE_SIZE`)
# - Color channels (3)
INPUT_SHAPE = [None, IMAGE_SIZE, IMAGE_SIZE, 3]

# The output shape of our model
OUTPUT_SHAPE = len(unique_breeds)

# Setup model URL from TensorFlow Hub
MODEL_URL = None  # Select a pre-trained model from TensorFlow Hub
```
