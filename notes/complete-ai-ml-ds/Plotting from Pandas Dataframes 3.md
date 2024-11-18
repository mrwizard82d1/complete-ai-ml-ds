Let's look at other plots 

Generate some random data and add it to a `DataFrame`

```python
x = rng.random((10, 4))
df = pd.DataFrame(x, 
				  columns=['a', 'b', 'c', 'd'])
```

Create a bar graph
```python
df.plot.bar()
plt.show()
```

- Plot has a legend
- Each row of the `DataFrame` is plotted in a different group of the bar graph
- As an alternative, we can use the `kind` parameter

```python
df.plot(kind='bar')
plt.show()
```

Let's make a bar plot using our `car_sales` data
- This code **does not** work

```python
car_sales.plot(x=car_sales['Make'], 
			   y=car_sales['Odometer (KM)'], 
			   kind='bar')  
plt.show()
```

- But this code **does** work (learn something new...)

```python
car_sales.plot(x='Make', y='Odometer (KM)', 
			   kind='bar')
plt.show()
```

Let's move on to another type of plot: a histogram

```python
car_sales['Odometer (KM)'].plot.hist()
plt.show()
```

- We seem to have a normal curve to the left with a couple of outliers
- An alternative
	- `car_sales['Odometer (KM)].plot(kind='hist')`
- The former call, `plot.hist()` allows one to specify the `bins` parameter
	- `car_sales['Odometer (KM)].plot.hist(bins=20)`
	- What is the best value for `bins`?
		- Not well-defined
		- **Experiment!**
	- One is trying to determine visually if one's data follows a well-know distribution
		- Like a normal or Gaussian but perhaps others

 