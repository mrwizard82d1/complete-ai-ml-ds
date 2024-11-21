We will build upon what we've already done by adding a subplot

Let's build a plot with two subplots
- One is cholesterol (y) by age (x)
- The other is 'thalach' (y - maximum heart rate) by age (x)

```python
fig, (ax0, ax1) = plt.subplot(nrows=2,
							  ncols=1,
							  figsize=(10, 10))
```

The first plot is similar to our previous code

```python
# Add data to axes 0  
scatter = ax0.scatter(x=over_50['age'],  
                      y=over_50['chol'],  
                      c=over_50['target'])  
  
# Customize ax0  
ax0.set(title='Heart Disease and Cholesterol Levels',  
        xlabel='Age',  
        ylabel='Cholesterol')  
  
# Add a legend to ax0  
ax0.legend(*scatter.legend_elements(), title='Target')  
  
# Add a meanline to ax0  
ax0.axhline(over_50['chol'].mean(),  
            linestyle='--',)
```

The second plot is similar to our first plot
```python
# Add data to axes 1 (ax1)
scatter = ax1.scatter(x=over_50['age'],
                      y=over_50['thalach'],
                      c=over_50['target'])

# Customize the axes
ax1.set(title='Heart Disease and Maximum Heart Rate Achieved',
        xlabel='Age',
        ylabel='Max Heart Rate')

# Add a legend to ax1
ax1.legend(*scatter.legend_elements(), title='Target')

# Plot the mean of ax1
ax1.axhline(over_50['thalach'].mean(),
            linestyle='--',)
```

Finally, we display the figure with its two subplots
```python
plt.show()
```

Can we tell them to share the x-axis?
- Two changes

```python
fig, (ax0, ax1) = plt.subplots(nrows=2,
							   ncols=1,
							   figsize=(10, 10),
							   sharex=True)

// ...

ax0.set(title='Heart Disease and Cholesterol Levels',
	    ylabel='Cholesterol')

// ...
```

Can we title the entire figure?
- Yes. Append this code before calling `plt.show()`.

```python
fig.suptitle('Heart Disease Analysis',
			 fontsize=14,
			 fontweight='bold')
```

