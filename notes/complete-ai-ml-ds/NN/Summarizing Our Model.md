What happens when we call `model.summary()`?

Review our output
- Type of our mode: sequential
- Two layers
- (Output) Shapes
- Parameter counts
	- Total
	- Trainable
	- Non-trainable
		- Because we are using **transfer learning**
		- These parameters have **already been learned** 
			- During the training of MobileNet v2
			- Learned by training of ImageNet
				- A collection of labeled images

Deep learning
- Each layer is a learning layer (a neural network of sorts) itself

Transfer learning
- Allows us to re-use the work done to train MobileNet V2
- And customize it to our specific problems
- And use our output layer to solve our problem

What are callbacks?
- We'll save that for the next video
- And then we'll create a function to train our video
