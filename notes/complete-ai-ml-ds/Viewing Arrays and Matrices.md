Introduction
- Search for documentation for `numpy.unique`

Viewing takes a bit of practice
- `a1[0]` returns a single item
- `a2[0]` returns the first **row** of a multi-row array
- `a3[0]` returns the first **matrix** of a multi-dimensional ()
- In general, a 1-dimensional `numpy` array is called a **vector**
- But for all dimensions above 1, the `numpy` array is called a **matrix**
- One can use array slices, for example, `a3[:2, :2, :2]`

Functions
- `unique()` - returns all **unique** elements of an `ndarray`