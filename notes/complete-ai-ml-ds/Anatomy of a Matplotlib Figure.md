The anatomy of a figure:
- Here's a picture

![[Anatomy-of-a-Matplotlib-plot.png]]

Terminology:
- A "figure" is the "blank canvas" (the whole thing)
- The previous figure has two "axes" plotted in two "subplots"
	- Axes 0
	- Axes 1
	- Share the x-axis
	- But two different y-axes (and "y-axis labels")
	- And two different "legends"
	- And two different "titles"
	- "figsize" - the size of the figure in inches (width, height) or (x, y)

Let's consider the "object-oriented" label
- Two key components of a figure
	- `matplotlib.figure.Figure`
	- `matplotlib.axes._axes.Axes`
- A figure can contain multiple axes
- The figure is the "base canvas"
- The axes are the thing on which we draw

Let's checkout a workflow in its entirety
0. Import `matplotlib` and prepare to plot in a `jupyter` notebook
1. Prepare data
2. Setup plot
3. Plot data
4. Customize plot
	- `title`
	- `xlabel`
	- `ylabel`
5. Save and show (you save the whole figure) 
	- `fig.savefig()`