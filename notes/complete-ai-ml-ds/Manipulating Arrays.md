A critical skill in machine learning is manipulating and comparing arrays

The `numpy` package supports array arithmetic between (compatible) arrays.
- Addition / Subtraction
- Multiplication - item by item (arrays with the same dimension)
- Multiplication - item by item with **broadcasting**
	- The arrays must have the same dimensions for all but the last
		- `a1 * a2`
		- Different shapes but compatible
		- `a1.shape == (3,)`
		- `a2.shape == (3, 2)`
	- Arrays that do not have same dimensions except the last
		- Raise a `ValueError`
- Division 
	- Arrays with the equal shapes
	- Arrays with compatible shapes (all but the last dimension)
- Floor division (`//`)
- Power
	- `a1 ** 2`
	- `np.power(a1, 2)`
- The `numpy` library has functions as arithmetic alternative
	- `np.square()`
	- `np.add()`
- Modulo
	- Operator `%`
	- `np.mod()`
- Exponentiation (`e ^ x`)
	- `np.exp(a1)`
- Natural logarithm (`ln(x)`)
	- `np.log(a1)`

  
