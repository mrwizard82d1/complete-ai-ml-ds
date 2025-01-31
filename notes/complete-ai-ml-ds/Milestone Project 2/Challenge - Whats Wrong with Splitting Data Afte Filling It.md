Hmm. We just split our data into training and test sets; however,
- We just split data in which we have **already** filled missing data
	- In other words, 
		- We filled in missing data in both
			- Training and
			- Validation sets
		- With data from both
			- Training and
			- Validation sets

We intend our validation set to represent the future
- But it now has "data" from the past

Our challenge now comes in two parts?

1. What does it mean if we fill our training data with information from the future (that is, the validation set)?
2. How might you implement a fix to the current way things are being done in the project?

Here are some key takeaways from a previous lecture:
- Encode/transform all categorical variables of your data
	- Use the entire data set.
	- This choice ensures that categorical variables are encoded the same
		- **Across** the training/test data
	- If you cannot do this
		- Ensure that the training and test sets have the **same column names**
- Split your data into training and test sets
- Fill the training and test set **numerical values** **separately**
	- That is, do not use data from the future (test set) 
	- To fill data from the past (training set)

Keeps these ideas in mind when we create a preprocessing function in a "few videos time"
- These ideas will help you answer questions in those videos, too
