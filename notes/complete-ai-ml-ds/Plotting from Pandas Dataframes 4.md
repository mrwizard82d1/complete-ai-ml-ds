We've done much plotting. How will I remember?

Let's try similar plots but on another data set
- `heart_disease = pd.read_csv('data/heart_attack.csv')`
- `heart_disease['age'].plot.hist()`

Let's try different binning values
- 20, 30, 50
- Plotting with 50 bins seems to identify outliers
	- More that 3 standard deviations away from the mean

Let's look at `subplots` in `pandas`
- `heart_disease.plot.hist(figsize=(10, 30), subplots=True)`

This solution is still not ideal. Many of the plots appear to have all the data bunched. This issues is a result of every plot **sharing** the same x-axis. We'll look at how to fix this in the next video using the object-oriented plotting methods.
