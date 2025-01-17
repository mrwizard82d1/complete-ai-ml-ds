We've found a logistic regression method that performed well, but we have additional work
- Hyperparameter tuning
- Feature importance
- Confusion matrix
- Cross-validation

Let's remind ourselves of metrics

| Classification Metrics | Regression Metrics             |
| ---------------------- | ------------------------------ |
| Accuracy $^{1}$        | $R^2$ (r-squared) $^{1}$       |
| Precision              | Mean absolute error (MAE)      |
| Recall                 | Mean squared error (MSE)       |
| F1                     | Root mean squared error (RMSE) |
$^{1}$ Default metrics in Scikit-learn

Additionally, we have
- Confusion matrix anatomy
- Classification report

Let's work on the following
- Hyperparameter tuning
- Feature importance
- Confusion matrix
- Cross-validation
- Precision
- Recall
- F1 score
- Classification report
- ROC curve
- Area under the ROC curve (AUC)

We'll focus on hyperparameter tuning
- Changing hyperparameters allow us to improve our fit
- **But also performs well on unseen data**

Let's train a number of `KNeighborsClassifier`s
```python
train_scores = []
test_scores = []

neighbors = range(1, 20 + 1) # From 1 to 20 neighbors
knn = KNeighborsClassifier()

for n in neighbors:
	knn.set_params(n_neighbors=n)

	knn.fit(X_train, y_train)

	train_scores.append(knn.score(X_train, y_train))
	test_scores.append(knn.score(X_train, y_train))
```

How might we visualize these scores?
```python
plt.plot(neighbors, train_scores, label='Training')
plt.plot(neighbors, test_scores, label='Test')

plt.title('KNN Classifier - Score versus Neighbors')
plt.xlabel('Number of Neighbors')
plt.ylabel('Model Score')
plt.legend()

# Plot x-ticks to make finding the maximum score neighbor count
plt.xticks(np.arange(1, 20 + 1, 1))

plt.show()
```

If we examine the maximum model score achieved
- We improved
- But we only see a maximum of 67%
- However, the maximum of both logistic regression and random forest regression is
	- **"Much" larger** than the KNN maximum
- Consequently, we **will no longer** try to improve the KNN classifier but will focus on
	- `LogisticRegression`
	- `RandomForestClassifier`

We've tuned KNN by hand
- Not very efficient (for the programmer)
- Let's try to tune the other models using `RandomizedSearchCV`

In the next video...
