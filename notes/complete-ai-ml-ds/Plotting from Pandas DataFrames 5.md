Our last plot was not ideal. We're going to try the object-oriented approach.

Which plotting technique/method should I use (pyplot versus matplotlib OO method)?
- Rule of thumb
	- When plotting something quickly, okay to use the `pyplot` method
	- When plotting something more advanced, use the OO method

Let's look in more detail at participants over 50
- `over_50 = heart_disease[heart_disease['age'] > 50]`

```python
over_50.plot(kind='scatter',
			 x='age'
			 y='chol'  # cholesterol
			 c='target');
```

- The resultant plot is okay but a bit tough to read

Let's try the OO plotting methods
```python
fig, ax = plt.subplot(figsize=(10, 6))
over_50.plot(kind='scatter',
			 x='age',
			 y='chol',
			 c='target',
			 ax=ax)
plt.show()
```

Let's try some additional adjustments
```python
fig, ax = plt.subplot(figsize=(10, 6))
over_50.plot(kind='scatter',
			 x='age',
			 y='chol',
			 c='target',
			 ax=ax)
ax.set_xlim([45, 100])
plt.show()
```

- This change results in additional whitespace around our data points but does not seem to clarify the plot itself

In general, the defaults offered by `matplotlib` are pretty good.

In the next video, we'll improve this plot.
