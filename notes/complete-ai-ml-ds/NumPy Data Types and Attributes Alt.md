Review our workflow
- Navigate to directory
- Start conda environment
	- `conda activate complete-ai-ml-ds`
- Create a new, empty jupyter notebook
	- `jupyter lab`

Start a new notebook
- `introduction-to-numpy.ipynb`

First step, import `numpy`
- `import numpy as np`
- A typical abbreviation

Remember, because I use the `vim` plugin for my notebooks, I must press `Esc` twice to get to the command mode
- One to exit `vim` insert mode
- One to exit the notebook command mode

The key `numpy` data type for AI, ML, and DS
- `ndarray`
	- N-dimensional array

Let's look at the anatomy of an array
- Note that the "`a3`" array in the lecture is actually a **2x3x3** array (or matrix)
	- Shape = (2, 3, 3)
- In the diagram, the `a3` array is a **3x3x2** array (or matrix)
	- Shape = (3, 3, 2)
- ![[Anatomy of an NumPy Array.png]]

Common `ndarray` properties
- `shape` - The size of the array along **each** axes
- `ndim` - The number of dimensions of an `ndarray`
- `dtype` - The "data type" of the `ndarray`
- `size` - The total number of items in the `ndarray`
- `type(an_array)` - The type of an `ndarray`
	- In this case, these arrays are all of type `numpy.ndarray`
	- Remember, all `ndarray` instances have the same (universal) type

`DataFrames` and `ndarrays`
- `pandas DataFrames` and `numpy.ndarrays` work well together
	- For example, `df = pd.DataFrame(a2)`
	- Creates a `DataFrame` whose:
		- Rows and columns are "labeled" with numbers
		- Items all have the same `dtype`
			- Typically one of the `numpy` numeric `dtypes`
			- 