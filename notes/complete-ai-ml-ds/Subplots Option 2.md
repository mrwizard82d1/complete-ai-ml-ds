Remember: **two** options for subplots
- We've already seen option 1

Option 2

```python
fig, ax = plt.subplots(nrows=2, ncols=2, figsize=(10, 5))
ax[0, 0].plot(x, x/2)
ax[0, 1].scatter(rng.random(10), rng.random(10))
ax[1, 0].bar(nut_butter_prices.keys(), 
			 nut_butter_prices.values())
 ax[1, 1].hist(rng.standard_normal(1000))
 plt.show()
```

- Daniel prefers option 1 because he feels that it uses clearer code

Although we've plotted from `numpy` arrays, most of our actual plotting will be from `pandas` `DataFrames`. Tune into the next video.
