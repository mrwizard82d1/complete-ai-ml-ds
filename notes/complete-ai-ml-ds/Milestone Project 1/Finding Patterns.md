We've found out about our data frame. We'll now compare data columns to one another.

We begin looking at heart disease and sex
- Remember, we are **exploring** the data
- `df['sex'].value_counts()`
	- Many more male than female

A convenient way to compare columns uses the `pd.crosstab()` function
- `pd.crosstab(df['target'], df['sex'])`
- Based on this data, women seem **much more likely** to have heart disease than men
	- 72 out of 96 versus 93 out of 207
	- Further, about 55% of all participants in our study have heart disease
		- That is, the number to beat is 55% for our model

Let's plot our cross-tabs
```python
pd.crosstab(df['target'], df['sex']).plot(
	kind='bar',
	figsize=(10, 6),
	color=['salmon', 'lightblue'],
)
plt.title('Heart Disease Frequency for Sex')
plt.xlabel('0 - No Disease', '1 - Disease')
plt.ylabel('Count')
plt.legend(['Female', 'Male'])
plt.show()
```

Currently, the 'target' value (0 or 1) is rotated 90% at the bottom of the x-axis
- `plt.xticks(rotation=0)`

Remember
- If we want to communicate clearly
- Then we must appropriately decorate our figures

Daniel encouraged us to perform our own exploration
- Investigated relationship between `heart disease` and
	- `cp` - Chest pain
	- `thalach` - maximum heart rate
- I seem to see an unexpected relationship between:
	- `heart disease` and `thalach`
		- Higher `thalach` seems more likely to have heart disease
- Hmm...
