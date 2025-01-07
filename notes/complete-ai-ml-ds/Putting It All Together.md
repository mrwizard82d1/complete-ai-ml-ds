Let's combine it all

We will use the `scikit-learn` `Pipeline` class
- See [scikit-learn Pipeline documentation](https://scikit-learn.org/stable/modules/generated/sklearn.pipeline.Pipeline.html)

Things to remember
![[Things to Remember.png]]

What would the "refinement process" look like?
- Import the data
- Review the data
	- Review column data types
		- Need all columns to be numeric	
	- Review missing data
		- Remove all missing values

Using a `Pipeline` (steps to do it all in one cell)
1. Fill missing data
2. Convert data to numbers
3. Build a model on the data

Steps
1. Import (many?) required packages
2. Import modeling packages
3. Set up default random number generator
4. Import data and drop rows with missing data
5. Define 
	 - The different features of our data set
	 - And the different transformers on features
6. Set up preprocessing steps
	 1. Fill missing values
	 2. Convert values to numbers
7. Create preprocessing and modeling pipeline
	- From the **existing** pipelines
8. Split the data
9. Fit and score

Now, we are performing our steps in a **single cell**
- Our experimentation uses "single-step" cells
- This last cell moves all those steps into **a single cell**

In the next video, we'll look at how to use
- Hyperparameter tuning
- In a **single cell**
