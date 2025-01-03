Correlation analysis
- What attributes have correlations?

For example,
- Size of lot and
- Size of floor space
- These values are highly correlated

We can remove these correlated attributes from our model
- Backward process
	- Train model on all attributes
	- Slowly remove attributes
	- Re-evaluate simpler model
- Forward process
	- Start with single column
	- Add columns until adding attributes **fails** to improve model
		- Find accuracy plateau
