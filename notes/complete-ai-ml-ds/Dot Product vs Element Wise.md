When would we ever want to use a transpose?
- The dot product

Let's "experiment" in our notebook
- Generate two random arrays
	- Integers in the range 0 <= value < 10
	- Array is size 5x3

Multiple arrays **element-wise**
- `mat1 * mat2`

Calculate the **dot-product**
- `np.dot(mat1, mat2)` raises a `ValueError`
	- `shapes (5, 3) and (5, 3) not aligned: 3 (dim 1) != 5 (dim 0)`

The difference between dot-product and element-wise
- See [Matrix Multiplication Explained](https://www.mathsisfun.com/algebra/matrix-multiplying.html) to read about multiplication
- See [live demo](http://www.matrixmultiplication.xyz) for a live demonstration of "the waterfall technique"
- Element-wise
	- Relatively simple
	- The two matrices must have identical dimensions (except in the last dimension)
	- Multiple each element (i, j) of the left-hand matrix by the same element (i, j) of the right-hand matrix
- Dot-product
	- The two matrices must have equal **inner dimensions**
	- Result is of size of **outer dimensions**
	- For example 
		- A 5x3 and a 3x5 matrix
		- A 3x3 and a 3x2
	- Multiplication occurs in row by column

Main take away
- The dot product is another tool in our toolkit
