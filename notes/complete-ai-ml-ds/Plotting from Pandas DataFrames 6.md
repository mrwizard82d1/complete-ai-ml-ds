Previously saw two different ways to plot
- `pyplot`
- `matplotlib` object-oriented method

Let's recreate figures using object-oriented method only

```python
## OO method from scratch
fig, ax = plt.subplots(figsize=(10, 6))

# Plot the data
scatter = ax.scatter(x=over_50['age'],
                     y=over_50['chol'],
                     c=over_50['target'])
# Customize the plot
ax.set(title='Heart Disease and Cholesterol Levels',
       xlabel='Age',
       ylabel='Cholesterol')

# Add a legend
ax.legend(*scatter.legend_elements(), title='Target')

# Let's add a horizontal line for the cholesterol mean
ax.axhline(over_50['chol']).mean(),
		   linestyle='--')

# Finally, show the figure
plt.show()
```

In general, using the full object-oriented API allows us to control **all** aspects of our plots