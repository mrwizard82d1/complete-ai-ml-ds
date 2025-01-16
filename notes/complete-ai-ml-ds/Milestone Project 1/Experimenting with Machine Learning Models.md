We are ready to evaluate our classifier models in our data, `heart_disease`

We calculate the scores for our models
- This calculation produces a warning
	- Apparently in our invocation of the `LogisticRegression()` model
	- We'll not address this issue now
	- In production code, we would address this issue

In our scenario, `LogisticRegression` provides the highest score

Let's quickly provide a visual comparison
```python
model_compare = pd.DataFrame(
	model_scores, 
	index=['accuracy'])
model_compare.T.plot.bar()
plt.show()
```
- Based on our graph, we will eliminate the KNN model

Next up
- We'll tune our model
	- Trying to get our model score >= 95%
- We'll calculate additional scores
