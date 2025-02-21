We broke down our `create_model()` function in the last video
- Passed the url to MobileNet v2
- But convert the output to the shape **we need**
- But what occurs in the call to `compile()`

The result of `compile()` is best explained with a story
- Here we are at the "Battle of the Hill"
- We are blindfolded
- Adam is at the bottom of the hill calling out instructions
- We have a judge to assess our journey

Less story
- We have a loss function
	- The lower the loss, the better we are doing
	- Adam, at the bottom of the hill, is helping us to minimize our loss
		- Adam is
			- A great general optimizer
			- Performs well on most tasks
	- The metrics are the judge
		- Tell us how well we have done
		- Evaluation
		- Remember, **many different choices for accuracy**
	

Common steps
- Define a model (layers)
- Define how the model will learn

Choosing a loss function depends on the problem we are solving:

|            | Binary classification | Multi-class classification |
| ---------- | --------------------- | -------------------------- |
| Activation | Sigmoid               | Softmax                    |
| Loss       | Binary cross-entropy  | Categorical cross-entropy  |

In the future,
- We will create **callbacks**
	- That is, actions our model can take **while learning patterns**
