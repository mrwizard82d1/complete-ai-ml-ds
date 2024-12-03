Original plan:
- Transform data first

New plan:
- Remove missing data

First step, ensure that all data is **numeric**
- Read our data set for this purpose
	- `./data/car_sales_extended.csv`
	- 1000 rows
	- Five `dtypes`
		- Three columns of type `int64`
			- `Odometer (KM)`
			- `Doors`
			- `Price`
		- Two columns of type `object`
			- `Make`
			- `Colour`

Split data into `X` and `y` (features and labels)
- `X = car_sales.drop('Price', axis=1)`
- `y = car_sales['Price']`

Split further into training and test
```python
X_train, X_test, y_train, y_test = train_test_split(X, y)
```

Remember our goal:
- Predict the sales price of a car
- Given the other data

Build machine learning model

```python
from sklearn.ensemble import RandomForestRegressor

model = RandomForestRegressor()  ## Create our model
model.fit(X_train, y_train)  ## Fit our model
model.score(X_test, y_test)  ## Score our model
```

- Note that we can create, fit, and score a model in a **very small** number of lines of code
	- The power of `sklearn`
- Unfortunately, our code throws an exception
	- "Exception: ValueError: could not convert string to float: 'Toyota'"

Remember, we **must** convert strings (objects) to numbers
```python
from sklearn.preprocessing import OneHotEncoder
from sklearn.preprocessing import ColumnTransformer

categorical_features = ['Make', 'Colour', 'Doors']
one_hot = OneHotEncoder()
transformer = ColumnTransformer(['one_hot', one_hot, categorical_features],
							   remainder='passthrough')
```

- The category, 'Doors', is "a bit tricky"
	- Remember, values of the 'Doors' column **cannot** be any value but only values in a limited set
		- Perhaps: 2, 3, and 4
		- Actually: 3, 4 and 5
			- `car_sales['Doors'].value_counts()`
- The column, `Doors`, is both **numeric**
	- It's (original) values are 3, 4, and 5
- But **also** categorical
	- It is **only** the values 3, 4, and 5

Our transformation (named `transformer`)
- Is named ('one_hot')
- Uses the `OneHotEncoder` transform (named `one_hot`)
- Applied to the features is `categorical_features`
- **Ignores** all other columns (`remainder='passthrough'`)

We create a new (`numpy`) array of (feature) values that has been transformed using `transformer`

What does "one hot encoding" even mean?
- Our original data

| Car | Colour |
| --- | ------ |
| 0   | Red    |
| 1   | Green  |
| 2   | Blue   |
| 3   | Red    |

- Is transformed to

| Car | Red | Green | Blue |
| --- | --- | ----- | ---- |
| 0   | 1   | 0     | 0    |
| 1   | 0   | 1     | 0    |
| 2   | 0   | 0     | 1    |
| 3   | 1   | 0     | 0    |

Now that our data is all numeric (zeros and ones), let's refit the model
- We (re-)initialize our random number generator for reproducibility of our work
```
import secrets

seed = secrets.randbits(128)
seed
```

- This cell prints '22232115356560702892793270496072236204'
```python
rng = np.random.default_rng(seed=22232115356560702892793270496072236204)
```

- Split our data, fit our model and score our model

```python
X_train, X_test, y_train, y_test = train_test_split(transformed_x, y, test_split=0.2)
model.fit(X_train, y_train)
model.score(X_test, y_test)
```

Although our score is not all that great (the maximum is 1), it is our first attempt
- We will look at **evaluation metrics** later

Our next topic: how to handle **missing** values
