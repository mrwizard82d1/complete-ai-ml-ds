Let's look into changing our style **within** a chosen style

Copy the "OO Method from scratch" cell and paste at the end
- Insert our selected style at the beginning of the cell
	- `plt.style.use('seaborn-whitegrid')`
- When we plot,
	- The dashed line is now red
	- The dots are no longer colored
	- But black and white and partial

Let's set the colormap (the `cmap` parameter of `scatter()`)
- `cmap='winter'`  ## or 'summer'
- We can now see the dots more clearly
- Consult the `matplotlib` tutorial for colormaps
	- It's all about experimenting
		- What do you prefer?
		- What best illustrates your point?

Let's check out how to constrain our plots to certain 
- Widths 
- Heights
- Copy our two-subplot example (cholesterol, age, and thalach)
- At first, this action simply uses our `seaborn` colormap
- But we want to change this colormap
	- `cmap='winter'`
- Looks good, but how can we clean up the "tiny area" between our leftmost and topmost grid lines and the respective plot border

Remove "tiny" grid regions at left and top
- We could change the appearance by changing the arguments to `ax0.set()` and `ax1.set()`
- But we'll use another mechanism
	- `ax0.set_xlim(50, 80)`
	- Remember that the two plots **share** the x-axis
	- The video calls `ax1.set_xlim(50, 80)`
		- This call is **not** 100% necessary
	- `ax1.set_ylim(60, 200)`

In the next video, we'll look at saving and sharing plots
