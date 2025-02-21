We've got a model and have already used it successfully

What does our code mean?
- "Sequential" - a linear stack of models
- First layer
	- Keras layer of `MODEL_URL`

What is "MobileNet V2"?
- See [Review: MobileNetV2 — Light Weight Model (Image Classification)](https://medium.com/towards-data-science/review-mobilenetv2-light-weight-model-image-classification-8febb490e61c)
- See [A Comprehensive Guide to Convolutional Neural Networks — the ELI5 way](https://medium.com/towards-data-science/a-comprehensive-guide-to-convolutional-neural-networks-the-eli5-way-3bd2b1164a53)

Understanding model details
- Read articles on MobileNet V2
- By default, this model produces 1280 output channels
	- However, we only need 120 (`OUTPUT_SHAPE`)
- We inform the model of this constraint by the parameter
	- `units=OUTPUT_SHAPE`

A beautiful aspect of transfer learning
- The architecture of MobileNet V2
	- Begins with an input layer with a shape of (224, 224, 3)
	- Ends with an output layer with a shape of (1, 1, 1280)
- But we only need 120 output items
	- Specifying the `units=OUTPUT_SHAPE` allows us to specify this number

What is a `Dense` layer (`keras.layers.Dense`)?
- Although the documentation might not be especially helpful
- I believe that a "dense layer" has connections 
	- From each item in the previous layer
	- To each item in the output layer

What is "activation"?
- Applying the `softmax` function (from Wikipedia)
	- Each component will be in the interval (0, 1)
	- The sum of all components will total 1
		- So they can be interpreted as probabilities

Which activation? Which loss?

|            | Binary classification | Multi-class classification |
| ---------- | --------------------- | -------------------------- |
| Activation | Sigmoid               | Softmax                    |
| Loss       | Binary cross-entropy  | Categorical cross-entropy  |
The final details of our `Dense` layer
- The `softmax` function
	- Helps us to convert the 1280 outputs of the MobileNet V2 model
	- To our output shape
		- (1, 1, 120)

But we'll learn more about that in the next video
