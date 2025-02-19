We'll check out TensorFlow Hub
- A library for reusable machine learning models
- Identifies projects useful for transfer learning
- Also
	- PyTorchHub
	- ModelZoo
	- PapersWithCode - Research in Deep Learning: papers **and** code

Unfortunately, no roadmap like [Online machine learning model map](https://scikit-learn.org/stable/machine_learning_map.html)

Although learning to build a model from scratch is valuable
- We will use an existing model first
- Once you have completed a project, then you may want to "start from scratch"

What can we do with TensorFlow Hub?
- Tutorials on how TensorFlow works
- Browse by **problem domain**
	- Our problem
		- Identify the breed of a dog given the image of a dog
- Now available on Kaggle
	- Keywords
		- Task: Image Classification
		- Image: image
		- Framework: Tensor Flow 22
	- These keywords seem to suggest
		- [Dog Breed Classification](https://www.kaggle.com/models/ameyjoshi0209/dog-breed-classification)
		- But maybe not
	- Fo example
		- Tesla using ResNet 50
- We will use
	- `imagenet/mobilenet_v2_130_224/classification`
	- Now found at https://www.kaggle.com/models/google/mobilenet-v2/tensorFlow2/130-224-classification

What have we done?
- Prepared our inputs
	- By loading our data
	- And converting it to tensors
- Picked a model from TensorFlow Hub to suit our problem domain
- Chosen our machine learning algorithm
- We have our output shape correct

Now we have to determine how to use all these things together
