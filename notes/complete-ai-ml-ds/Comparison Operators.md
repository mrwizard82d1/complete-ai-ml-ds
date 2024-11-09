Notebooks support typical comparison operators
- All operators require "compatible" operands
	- Operators utilize "broadcast"
- Greater than `>`
	- Because we are comparing two `ndarrays` 
		- Comparisons operate element-by-element
	- Returns another `ndarray`
		- Each element is the result of the element-by-element comparison
- Greater than or equal `>=`
- Greater than a constant `a1 < 5`
- Less than a constant `a1 > 5`
- Equality `a1 == a1`
- Equality between compatible arrays: `a1 == a2`
	- Utilizes broadcast

Documentation
- Search for `numpy comparison operators`


