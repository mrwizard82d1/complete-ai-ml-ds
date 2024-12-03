What if I have **missing** data?

Two main techniques
1. Replace missing values with some other value
	- AKA "imputation"
2. Remove the samples with missing data altogether

Neither of these techniques is "perfect"
- Replace some, possibly significant, data with something else
- Remove the samples completely (less data in total)

"Missing data"
- Different samples have data missing from different columns
- For example,  `./data/car-sales-extended_missing_data.csv`

Load data set with "missing" data
- `car_sales_missing = pd.read_csv('./data/car-sales-extended-missing-data.csv')`

H2 quickly find missing data loaded into a `DataFrame`
- This technique takes advantage of Python coercion:
	- `True` coerced to 1
	- `False` coerced to 0
- `car_sales_missing.isna().sum()`

Separate our imported data into "features" and "values" (`X` and `y`)

```python
X = car_sales_missing.drop('Price', axis=1)
y = car_sales_missing['Price']
```

Let's try to convert our data to numbers

```python
from sklearn.preprocessing import OneHotEncoder
from sklearn.compose import ColumnTransformer

categorical_features = ['Make', 'Colour', 'Doors']
one_hot = OneHotEncoder()
transformer = ColumnTransformer\
([('one_hot',
   one_hot,
   categorical_features)],
  remainder='passthrough')

transformed_X = transformer.fit_transform(X)
transformed_X
```

At this point in the video, Python raises an exception
- "Value Error: Input contains NaN"
- However, since I'm using `sklearn` version 1.5.x
	- I **do not** see this error
	- But I'll pretend that I do

Two options to fill data
1. Fill missing data with `pandas`
	- For example
		- Text values with "missing"
		- 'Odometer (KM)' with mean of same column
		- 'Doors' with the most common value (4)

```python
car_sales_missing['Make'] = car_sales_missing['Make'].fillna('missing')

car_sales_missing['Colour'] = car_sales_missing['Colour'].fillna('missing')

car_sales_missing['Odometer (KM)'] = car_sales_missing['Odometer (KM)'].fillna(color_sales_missing['Odometer (KM)'].mean())

car_sales_missing['Doors'] = car_sales_missing['Doors'].fillna(4)
```

2. Remove rows with missing data
	- For example, this strategy is useful for the `Price` column
		- `car_sales_missing = car_sales_missing.dropna(subset=['Price'])`

Finally, we again "test" for `None` or `NaN`
- `car_sales_missing.isna().sum()`

Now that we've eliminated our missing values, let's rerun our model fit
- Remember, we must split our data **first** (since we've changed it)

```python
X = car_sales_missing.drop('Price', axis=1)
y = car_sales_missing['Price']
```

- And then we transform it
```python
from sklearn.preprocessing import OneHotEncoder
from sklearn.compose import ColumnTransformer

categorical_features = ['Make', 'Colour', 'Doors']
one_hot = OneHotEncoder()
transformer = ColumnTransformer\
([('one_hot', one_hot, categorical_features)],
 remainder='passthrough')

transformed_X = transformer.fit_transform(car_sales_missing)
transformed_X
```

In the next video, we'll see to to fill values using pure Scikit-Learn
