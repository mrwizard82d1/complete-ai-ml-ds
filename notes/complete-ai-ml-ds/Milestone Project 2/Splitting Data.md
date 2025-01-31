We scored our model but...
- Why is our metric score **not reliable**
- We trained our model on some data
	- But then we evaluated it **on the same data**

We trained our model on 
- Training data
- **And** validation data
- The reason
	- So that we can create validation data ourselves

H2 create validation data?
- We need to split our data into training and validation sets
- We originally loaded **both**
- Based on the documentation for the data set, 
	- We can create a similar validation set by splitting our data
		- All data with `saleyear == 2012` will be our validation data
		- All other data will be our training data

Split data into training and validation sets
```python
df_valid = df_tmp[df_tmp.saleyear == 2012]
df_train = df_tmp[df_tmp.saleyear != 2012]
```

Split into X and y (features and labels)
```python
X_train, y_train = (
	df_train.drop('SalePrice', axis=1), df_train['SalePrice']
)
X_valid, y_valid = (
	df_valid.drop('SalePrice', axis=1), df_valid['SalePrice']
)
```

We've now created a train and validation set
- Time to build more models

Must figure out how to evaluate our machine learning model
- In the next video
