We start by cleaning up our data frame
- Convert prices to integers and remove last two digits
	- `car_sales['Price'] = (car_sales.str.replace('[$,.]','', regex=True)
	- `car_sales['Price'] = car_sales['Price'].str[:-2]`

Add a sale date column
- `car_sales['Sale Date'] =Lpd.date_range('1/1/2024', periods=len(car_sales))`

Calculate our total sales
- `car_sales['Total Sales'] = car_sales['Price'].cum_sum()`
- Oops! We discovered that our 'Price' column is still a **string**
- Consequently, `cumsum()` simply **appends** each price throughout the data frame

To correct this issue, we must convert the type of the 'Price' column
- Insert `astype(int)` **before** calling `cumsum()`

Let's plot the 'Total Sales'

```python
car_sales.plot(x='Sale Date', y = 'Total Sales')
plt.show()
```

This is an example of leveraging the documentation
- Earlier, we used code taken **directly** from 
	- Documentation
	- Another example we found online
- Replicated example code
- Then take principles from example code and combine with our own data to accomplish a goal that is important to us

These steps exemplify a workflow that one can apply to your own work on projects
- Search
- Try to find examples 
- Take information from that example
- Seeing if you can apply what you've learned to your specific problem to accomplish a useful goal

How about we try a scatter plot?
- `car_sales.plot(x='Odometer [KM)', y='Price', kind='scatter')`
- Hmm. The video presented an error executing this code
	- However, my execution **worked**
		- Is it plotting against a string?
- Looking back, the problem is that our code only converted the 'Price' column to an `int` as part of the expression used to invoke `cumsum()`
- We must actually **transform** the 'Price' column to a numeric field
	- `car_sales['Price'] = car_sales['Price'].astype(int)`

We have seen a couple of examples of "directly" plotting from a `pandas` `DataFrame`
