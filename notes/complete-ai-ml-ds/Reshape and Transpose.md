H2 change the **shape** of an `ndarray`?

What happens if one executes `a2 * a3`?
- **Fails**
- "Operands could not be broadcast together with shapes (2, 3) (2, 3, 3)"

To make the multiplication work, we must **add** a dimension to `a2`
- `a2.reshape(2, 3, 1)` - Added a new dimension of size 1
- Allows us to multiply the reshaped `a2` with `a3`
- See [Array Broadcasting in Numpy](https://numpy.org/doc/1.20/user/theory.broadcasting.html)

Important rule
- Just because your `numpy` array comes in one shape, it need not **remain** in that shape
	- A shape mismatch often produces the "could not be broadcast together with shapes"

Transpose
- Switch rows and columns of a 2-dimensional `ndarray`
- In more general terms, permutes **any number of axes** of an `ndarray`
- See [the documentation for `np.transpose`](https://numpy.org/doc/stable/reference/generated/numpy.transpose.html)
