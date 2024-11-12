Step through our "getting started" workflow
- Refresh our knowledge

Start new `jupyter` notebook
- Name: "Introduction to Matplotlib"

First steps
- Inline interactive plots
	- `%matplotlib inline`
	- **Note** executing this line seems to break the expected behavior
		- In other words, I want to execute my `matplotlib` plots in-line in my notebook. 
		- Unfortunately, if I execute this `inline` command, the plots **do not appear** in the current version of `jupyter-lab`
			- I suspect I would need to follow my call to 
				- `plt.plot()`
				- With a call to `plt.show()`
				- To restore the expected behavior
		- Therefore, I have removed it in my notebook
- Import what we need
	- `import numpy as np`
	- `import matplotlib.pyplot as plt`
	- `import pandas as pd`
	- (`import polars as pl`)
	- `import sklearn`

Our first (empty) plot:
- `plt.plot()`
- To remove the brackets otherwise printed
	- Terminate the call with a semicolon (';')
	- An alternative to the semicolon is the two commands (in one cell)
		- `plt.plot()`
		- `plt.show()`

Actually plotting data:
- `plt.plot([1, 2, 3, 4])` plots the y-values, 1, 2, 3, and 4 against **implied** x-values (0, 1, 2, 3)
- If we create x- and y-values
	- `x = [1, 2, 3, 4]`
	- `y = [11, 22, 33, 44]`
	- `plt.plot(x, y)`

This process so far is the so-called "stateless" way of plotting
- This approach is also the approach taken by Matlab
- **Remember**, "the pylot API is generally less flexible than the object-oriented API." (From the Matplotlib Pyplot tutorial)
	- From the newer [documentation](https://matplotlib.org/stable/tutorials/pyplot.html#sphx-glr-tutorials-pyplot-py)
		- "The implicit pylot API is generally less verbose but also not as flexible as the explicit API."

Read [The Lifecycle of a Plot](https://matplotlib.org/stable/tutorials/lifecycle.html#sphx-glr-tutorials-lifecycle-py) tutorial.

Three methods for plotting
- First

```python
fig = plt.figure()  ## create a figure
ax = fig.add_subplot()  ## create a single set of axes
plt.show()
```

- Second

```python
fig = plt.figure()  ## create a figure
ax = fig.add_axes([1, 1, 1, 1])  ## add axes with a bounding rectangle of specified size
ax.plot(x, y)  ## add some data
plt.show()
```

- Third (recommended)

```python
fig, ax = plt.subplots()  ## creates a figure and a set of subplots (each with its own axes)
ax.plot(x, y)  ## plot data using axes
plt.show()
```

- Remember, one can **regenerate** a plot by simply changing the x- and y-values supplied to `ax.plot()`
