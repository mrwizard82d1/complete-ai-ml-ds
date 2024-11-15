Many plots are built off pure `numpy` arrays

Making figures with `numpy` arrays
- Create some linearly spaced data
	- `x = np.linspace(0, 10, 100)`
		- 100 points
		- >= 0
		- <= 10
	- `np.linspace` returns
		- `num` linearly spaced samples 
		- Over the interval `[start, step]`

Common plot types:
- Line
- Scatter
- Bar
- Histogram
- Subplot (not really a plot type)

Plot the data (using a **line plot**)
- `fig, ax = plt.subplots()`
- `ax.plot(x, x**2)`

Use the same data to create a scatter plot
- Exponential
	- `fig, ax = plt.subplot()`
	- `ax.plot(x, np.exp(x))
- Sinusoidal
	- `fig.ax = plt.subplot()` 
	- `ax.plot(x, np.sin(x))`

Make a plot from a dictionary
- Recreate our `nut_butter_prices` from earlier
- `fig, ax = plt.subplot()`
- `ax.bar(nut_butter_prices.keys(), nut_butter_prices.values())`
- `ax.set(title="Dan's Nut Butter Story, ylabel=Price ($))`
- `plt.shoW()`
