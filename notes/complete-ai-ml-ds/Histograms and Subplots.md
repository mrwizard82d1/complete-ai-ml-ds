Hopefully, you have created your own graphs

Horizontal bar graph
```python
fig, ax = plt.subplots()
ax.barh(nut_butter_prices.keys(), nut_butter_prices.values())
plt.show()
```

- The video encounters an issue with my code
	- The work around was to wrap both arguments to `ax.barh()` in `list()`
	- It appears this "fix" is no longer needed

Histogram
- Initialize a random number generator for our notebook
	- `import secrets` and generate a 128-bit seed
	- `rng = np.random.default_rng(seed)` (from above)
	- `x = rng.standard_normal(1000)` - 1000 samples from a normal distribution
- Plot the histogram of these random values

```python
fix, ax = plt.subplots()
ax.hist(x)
plt.show()
```

Plotting **multiple plots** at the same time
- **Subplots**!
- Two options
	- Create a 2x2 array of axes in a figure with a size of 10x5
	- Plot **different** plots on each axes

```python
fig, ((ax1, ax2), (ax3, ax4)) = \
	plt.subplot(nrows=2 ncols=2, figsize=(10, 5))
ax1.plot(x, x/2)
ax2.scatter(rng.random(10), rng.random(10))
ax3.bar(nut_butter_prices.keys(),
	    nut_butter_prices.values())
ax4.hist(rng.standard_normal(1000))
plt.show()
```

- You could add additional information to the plot on each axes
	- `title`, `xlabel`, `ylabel`, etc.

We'll look at option two for plotting multiple plots in the next video
