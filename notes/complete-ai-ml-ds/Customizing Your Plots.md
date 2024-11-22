We've seen how to create complex plot but have glazed over the details.

We want to transform our current plot to be similar to the plot

![[Anatomy-of-a-Matplotlib-plot.png]]

Let's look at `matplotlib` styles
- `plt.style.available`
- This reports all styles currently available to us

Let's investigate these styles
- To use a style
	- `plt.style.use()`
- Experiment with
	- 'seaborn-v0_8-whitegrid'
	- 'seaborn-v0_8'

Let's try another kind of plot
 - `car_sales.plot(x='Odometer (KM)', y='Price', kind='scatter')` 

And another style
- `plt.style.user('ggplot')`
- `car_sales['Price'].plot();`

How to change the style, legend, and so on
- Let's customize our plot with the `set()` method

```python
# Customize our plot with the `set()` method  
ax = df.plot(kind='bar')  
  
# Add some labels and a title  
ax.set(title='Random Number Bar Graph from DataFrame',  
       xlabel='Row Number',  
       ylabel='Random Number')  
  
# Make legend visible (a no-op because our legend is already visible)  
ax.legend().set_visible(True)  
  
plt.show()
```

What if the set style does not quite fit?
- See the next video
