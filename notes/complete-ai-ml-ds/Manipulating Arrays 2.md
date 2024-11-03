Time to learn about manipulating arrays through **aggregation**

Meaning of **aggregation**
- "The formation of a number of things into a cluster"
- Performing the same operation on a number of things

Python provides some methods to aggregate
- For example, the Python `sum()` function can be applied to a Python `list`

But remember, `numpy` has its **own** implementation of these methods
- `np.sum()`

Difference between `sum()` and `np.sum()`
- Rule of thumb
	- Use Python functions, for example, `sum()`, on Python datatypes`
	- Use NumPy functions like `np.sum()` on NumPy arrays
- Use `%timeit` to benchmark calls
	- Python `sum()` took about 4 ms (milliseconds) on `massive_array`
	- But NumPy `sum()` took about 20 $\mu$s (microseconds)

Reinforces our "rule of thumb"
- When working with NumPy use `numpy` functions
- When working the Python data structures, you can use Python functions

Other functions
- `np.mean()` The arithmetic mean of a sequence
- `np.max()` The maximum value of a sequence
- `np.min()` The minimum value of a sequence
- `np.var()` The variance of a sequence
- `np.std()` The standard deviation of a sequence
