We currently have path names for our images

Our goal: turn our data into tensors
- Let's turn our labels into numbers
```python
labels = np.array(labels)

# An alternative
# labels = labels_csv['breed'].to_numpy()
```
- This assignment produces a `numpy` array with 10,222 items
- See if we missing label by comparing
	- The number of labels to
	- The number of filenames

But a machine learning model **cannot** take strings
- Requires numbers
- Identify unique labels
```python
unique_breeds = np.unique(labels)
```
- We observe 120 unique breeds

Let's turn `labels` into an array of Boolean values
- We experiment:
```python
print(labels[0])
# Takes advantage of broadcasting
labels[0] == unique_breeds
```
- Returns an array of Booleans
	- But item 20 is `True`!
- Repeat similar logic for all our labels
```python
boolean_labels = [label == unique_breeds for label in labels]
boolean_labels[:2]
```

H2 turn our boolean array into **integers**
- Some experiments
```python
# Original label
print(labels[0])

# Index of `labels[0]` in `unique_breeds`
print(np.where(unique_breeds == labels[0]))

# Index where the maximum (that is, `True`) occurs
print(boolean_labels[0].argmax())

# Convert labels to integers
print(boolean_labels[0].astype(int))
```
- Similarly
```python
print(labels[2])
print(boolean_labels[2].astype(int))
```

We need to split our data into
- Training
- Validation
- We'll accomplish this task in the next video
