We have an "ideal model" that performs well in our tests
- Performs well against Kaggle evaluation metric
- Let's now **make predictions on test data**

Let's load our test data
```python
df_test = pd.read_csv(
	'data/bluebook-for-bulldozers/Test.csv',
	low_memory=False,
	parse_dates=['saledate'],
)
```

And immediately try running our tests:
```python
test_preds = ideal_model.preduct(df_test)
```
- **Fails** (raises a `ValueError` exception)
- Raises an exception because
	- Our training and validation data **was preprocessed**
	- But our test data **is raw**
- Must perform same preprocessing 
	- On test data
	- That we performed on training and validation data

Test data:
- Has missing data
```python
df_test.isna().sum()
```
- Contains non-numeric data
```python
df_test.info()
```

To address this issue, we must perform the **same** preproccesing
- On our test data
- That we performed on the training and validation data

Our solution
- Encapsulate our preprocessing steps **in a function**
```python
def preprocess_dataset(df):
	# Add some additional columns for date "pieces"
	df['saleyear'] = df['saledate'].dt.year  
	df['salemonth'] = df.saledate.dt.month  
	df['saleday'] = df.saledate.dt.day  
	df['saledayofweek'] = df.saledate.dt.dayofweek  
	df['saledayofyear'] = df.saledate.dt.dayofyear
	
	# Drop the "label" column
	df.drop('saledate', axis=1, inplace=True)

	# Convert object columns to strings
	# Not in video but now needed
	columns_to_convert = [label for
	                      label in df.columns  
	                      if df[label].dtype == 'object']  
	for label in columns_to_convert:  
	    df[label] = df[label].astype('string')
	    
	# Convert all our `string` columns to data categories
	for label, content in df.items():  
	    if pd.api.types.is_string_dtype(content):  
	        df[label] = content.astype('category').cat.as_ordered()
        
	# Fill missing values in numeric columns with median value
	for label, content in df.items():  
	    if pd.api.types.is_numeric_dtype(content): 
	        if pd.isnull(content).sum():  
	            # Add a binary column which tells us if data is missing  
	            # This action allows us to **remember** if we filled
	            # missing values with the median
	            df[label + '_is_missing'] = pd.isnull(content)  
	  
	            # Fill missing numeric values with median  
	            # Using median because median is more robust
	            # against outliers.
	            df[label] = content.fillna(content.median())

	# Turn categorical values into numbers and fill missing  
	for label, content in df.items():  
	    if not pd.api.types.is_numeric_dtype(content):  
	        # Add a binary column to indicate missing data  
	        df[label + '_is_missing'] = pd.isnull(content)  
	  
	        # Turn categories into numbers **but add 1**  
	        # Add one because the `Categorical` dtype encodes
	        # missing values as **-1**. Adding 1 means that all 
	        # our values are non-negative.
	        df[label] = pd.Categorical(content).codes + 1
	
	return df
```

 A good question: where might this function break?
- We'll answer this question in the next video
