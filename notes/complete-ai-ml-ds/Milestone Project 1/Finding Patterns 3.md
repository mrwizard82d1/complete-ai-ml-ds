We've done a bit of EDA (Exploratory Data Analysis)
- Now let's build a **correlation matrix**

What is a **correlation matrix**?
- Informal
	- A table of numbers that describe independent variables relate to each other

Calculate
```python
# Calculates the (default) pairwise correlation matrix between all columns
df.corr()
```
- Kind of helpful but lots of numbers

Let's plot the matrix using a heat map to try to help our understanding
```python
correlation_matrix = df.corr()

fig, ax = plt.subplots(figsize=(15, 10))
ax = sns.heathmap(
	correlation_matrix,
	annot=True, # annotate the heat map
	linewidths=0.5,
	fmt='.2f', # only show two decimal places
	cmap='YlGnBu', # yellow-green-blue color map
)
```
- Video adjusted limits; my version of seaborn / matplotlib plotted without adjustment
```python
bottom, top = ax.get_ylim()
ax.set_ylim(bottom + 0.5, top - 0.5)
```

Next, we want to do next is **model-driven EDA**
- Deriving a machine learning model to give us insights into how the independent variables affect the dependent variables
- Finally, machine learning!
