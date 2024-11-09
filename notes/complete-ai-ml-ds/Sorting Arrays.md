Sorting an array of numbers

Use `random_array`
	- Regenerate `random_array = np.random.integers(10, size=(5, 3))`

What if we want to sort `random_array`?
- Use `np.sort(random_array)`

Another sort function, `np.argsort()`
- Returns the **indices** that would sort an array

A related function, `np.argmin()`
- Returns the **index** of the minimum value of an array
- This function **flattens** the array before calculating this value

A similar related function, `np.argmax()`
- Returns the **index** of the maximum value of an array
- With no axis specified, the array is **flattened** and the returned value is the **single index** of the maximum (minimum) value
- 