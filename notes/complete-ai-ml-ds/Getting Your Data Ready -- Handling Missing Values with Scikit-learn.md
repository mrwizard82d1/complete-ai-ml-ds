Saw how to fill data
- Using `pandas`
- And convert to numbers using Scikit-Learn

Now let's see how to more simply use a single library (Scikit-Learn)

Read data as usual
- `car_sales_missing = pd.read_csv('./data/car-sales-extended-missing-data.csv')`

Check for missing data
- `car_sales_missing.isna().sum()`

Remove rows with **missing labels**

```python
car_sales_missing = \
	car_sales_missing.dropna(subset=['Price'])
```

Split into features and labels

```python
X = car_sales_missing.drop('Price', axis=1)
y = car_sales_missing['Price']
```

H2 fill missing data with `Scikit-Learn`
- Import needed classes
	- `SimpleImputer`
	- `ColumnTransformer`
- Create needed imputers
	- Fill missing
		- Categorical values with 'missing'
		- Door values with 4 (the most likely value)
		- Numeric values with the mean of all values in the column
- Identify the columns in our data to which to apply the imputers
- Create an overall imputer to transform each column appropriately
- It works! (At least no errors)

Check as we have done previously

```python
car_sales_missing = \
	pd.DataFrame(filled_X, 
				 columns=['Make', 'Colour',
						  'Doors', 'Odometer (KM)'])
car_sales_missing.isna().sum()
```

We now have **no** missing values

We can now convert all our data into numbers using previous code in notebook

```python
from sklearn.preprocessing import OneHotEncoder  
from sklearn.compose import ColumnTransformer  
  
categorical_features = ['Make', 'Colour', 'Doors']  
one_hot = OneHotEncoder()  
transformer = ColumnTransformer([('one_hot', one_hot, categorical_features)],  
                                remainder='passthrough')  
  
transformed_X = transformer.fit_transform(car_sales_missing)  
transformed_X
```

The current status of our transformed data
- All **numeric**
- Filled (no missing data)

Let's fit a model

Typical steps
- Remember to start by setting a specific seed to the `numpy` `default_rng`
- Import our regressor and models
- Split our data
- Create our model
- Fit our model on training data
- Score our fitted model on test data

```python
from sklearn.ensemble import RandomForestRegressor
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = \
	test_train_split(transformed_X, y, test_size=0.2)

model = RandomForestRegressor()
model.fit(X_train, y_train)
model.score(X_test, y_test)
```

Remember, video gets warning that goes away in Scikit-Learn 0.22

Note: the video compares
- `len(car_sales_filled), len(car_sales)`
- I believe that comparison is incorrect
	- No `car_sales_filled`
- Actually compare
	- `len(car_sales_missing), len(car_sales)`

In video,
- Because we have **dropped** missing samples, 
	- Our score has **also dropped**

Future video
- What was the reason for choosing a `RandomForestRegressor`?
- Tune in tomorrow to hear Daniel say...
