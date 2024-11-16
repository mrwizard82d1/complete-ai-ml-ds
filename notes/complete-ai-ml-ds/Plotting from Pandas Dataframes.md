Have demonstrated different plots in recent videos
- But, more often than not, one will be plotting from
	- `pd.DataFrame`
	- **Not** `np.array`

Import `pandas` (and `polars`)
- Make a data frame
	- `car_sales = pd.read_csv('data/car_sales.csv')`
	- `car_sales_pl = pl.read_csv('data/car-sales.csv')`

Plot a random `Series`

```python
ts = pd.Series(rng.standard_normal(1000),
			   index=pd.date_range('1/1/2020', 
			   periods=1000))
ts = ts.cumsum()  ## Calculate cumulative sum
ts.plot()
plt.show()
```

Similarly, we can create a similar plot using `polars`

```python
from datetime import date
tsp = pl.DataFrame({
	'price': rng.standard_normal(1000),
	'date': pl.date_range(date(2020, 1, 1),
						  date(2022, 9, 26),
						  "1d",
						  eager=True)})
tsp = tsp.with_columns(
	pl.col('price').cum_sum().alias('cum')
)
fig, ax = plt.subplots()
ax.plot(tsp['date'], tsp['cum'])
plt.show()
```

