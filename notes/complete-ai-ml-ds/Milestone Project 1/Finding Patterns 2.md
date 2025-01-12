For our next comparison, we might try to combine a couple of our variables
- For example, 
	- `age`
	- `thalach`
	- Against `target`

Let's investigate `thalach`
- Has many different values
- Consequently, a bar graph may not be the best way to visualize the data

What is `thalach`?
- From our data dictionary
	- "thalach: maximum heart rate achieved"

Our investigation is **exploratory**
* The key goal is **discovery**

Lets investigate
- Age versus
- Max Heart Rate Achieved
- For Target

Because we have **two** independent variables, we may need to create two plots
- We only look at "positive" (`target == 1`) samples
```python
plt.figure(figsize=(10, 6))

plt.scatter(df.age[df.target == 1],
		    df.thalach[df.target == 1],
		    c='salman')

plt.show()
```
- One might infer that `thalach` decreases with age (with heart disease)

Now we add the "negative" samples
```python
plt.figure(figsize=(10, 6))

plt.scatter(df.age[df.target == 0],
		    df.thalach[df.taget == 0],
		    c='lightblue')

plt.show()
```

Both plots
- Seem to have a downward slope
- But difficult to discern a clearer pattern

Add some helpful information to better communicate the plot
```python
plt.title('Heart Disease Against Age and Max Heart Rate')
plt.xlabel('Age')
plt.ylable('Max Heart Rate')
plt.legend(['With Heart Disesase', 'No Heart Disease'])
```

What's the distribution of the age?
- Plot the distribution with a histogram
```
df.age.plot.hist()

plt.show()
```
- Age seems kind of "normal"
	- But swaying to the right
	- With a cut off around 80
	- No obvious data to clean up
		- No obvious outliers

Let's look at chest pain (`cp`) versus heart disease (`target`)
- `pd.crosstab(df.cp, df.target)`
- Seems to have a relationship
	- But perhaps surprising
		- Non-anginal pain has many patients with heart disease
- Probably want to discuss all apparent relationships with a subject matter expert

Let's make the crosstab more visual.
```python
pd.crosstab(df.cp, df.target).plot(kind='bar',
								   figsize=(10, 6),
								   color=['salmon', 'lightblue'])

plt.title('Heart Disease Frequency Per Chest Pain Type')
plt.xlabel('Chest Pain Type')
plt.ylabel('Amount')
plt.legend(['With Heart Disease', 'No Heart Disease'])
```
- Again prompts a question for our expert
	- "What's the reason for the high non-anginal pain?"

In the next video, we'll begin looking at correlation
- Between independent
- And our dependent variable
- We'll use a **correlation matrix**
