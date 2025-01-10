Our tools are ready to go; now we load and explore our data

Load data
```python
df = pd.read_data('data/heart-disease.csv')
df
```

Data exploration (exploratory data analysis or EDA)
- Goal: become a SME on the data set with which you are working
- Steps
	1. What question(s) are you trying to solev?
	2. What kind of data do we have and how do we treat different types
	3. What's missing from the data and dow do you deal with it?
	4. Where are the outliers and why should you care about them?
	5. How can you add, change, or remove features to get more out of your data?

Start by looking at our label (the `target` column)
- Let's find out how many of each class we have
```python
df['target'].value_counts()
```
- The result, 165 1's and 138 0's, are fairly balanced

We can test this idea by plotting the histogram of the `target` values
```python
df['target'].value_counts().plot(kind='bar', color=['salmon', 'lightblue'])
```

Let's peruse our other columns
```python
df.info()
```
- What data is in other columns?
- What columns are missing data?
- What types of data do we have?
- What might column names mean?
	- Check data dictionary

Process of investigating is **opportunistic** 
- **Not** deterministic

Look for missing data
```python
df.isna().sum()
```

Additional descriptive information
```python
df.describe()
```
- Count
- Mean
- Std (standard deviation)
- Min
- 25%
- 50%
- 75%
- Max

Next step: compare different columns (in the next video)
