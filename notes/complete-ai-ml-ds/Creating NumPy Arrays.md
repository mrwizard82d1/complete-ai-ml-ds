H2 create `numpy` arrays (`ndarray`)

Use `np.array()` passing a `list` of numbers as the argument

Use `np.ones()`
- Accepts 
	- A `shape` argument
	- A `dtype` argument
	- A `order` argument: a string
		- Fill array in column major ('C') order
		- Or in FORTRAN ('F') order

Use `np.zeros()`
- Details similar to `np.ones()` but for filling the array with zeros (0)
- One often uses `np.zeros()` to create an array with the appropriate **shape** but fill in the data later

Use `np.arange()` to create a sequence of values
- Single argument is `stop` 
- Three arguments are `start, stop, step` 
	- `step` is also optional defaulting to 1
- Also supports `float` arguments but...
	- Beware floating point addition etc.

Use `np.random.randint()`
- Creates an `ndarray` 
	- Of a specified shape
	- And filled with random integers in a range
		- The range is defined by the required value `low`
		- And the optional value `high`

Use `np.random.random()`
- Creates an `ndarray` with specified **shape only**
- Similar to `np.random.randint()`

The function `np.random.rand()` is:
- A convenient alias for `np.random.random()`
	- For folks coming from Matlab
- Takes a number of `int` arguments defining the dimensions of the newly created `ndarray`

**Beware** the numbers returned by `np.random.random()`
- Are not random
- But **pseudo-random**
- Setting the random number seed to a specific value generates the same "random" sequence over time
	- `np.random.seed(3)`
	: