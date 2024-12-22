Evaluating the results of a machine learning model is as important as building it
- However, different machine learning models
	- Have **different** evaluation metrics

#### Classification Model Evaluation Metrics/Techniques ####

- **Accuracy** 
	- The accuracy of a model in decimal form
	- Perfect accuracy is 1.0
- [**Precision**](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.precision_score.html#sklearn.metrics.precision_score)
	- The proportion of positive identifications which were actually **correct**
		- Model  predicts class 1; target class 1
	- **No false positives** => precision == 1.0
- [**Recall**](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.recall_score.html#sklearn.metrics.recall_score)
	- The proportion of **actual positives** that we correctly classified
	- **No false negatives** => recall == 1.0
- [**F1 score**](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.f1_score.html#sklearn.metrics.f1_score)
	- A combination of precision and recall
	- A perfect model achieves an F1 score of 1.0
- [**Confusion matrix**](https://www.dataschool.io/simple-guide-to-confusion-matrix-terminology/)
	- Compare predicted values with actual values in a tabular way.
	- If 100% correct, all values will be on the top-left to bottom-right diagonal
- [**Cross-validation**](https://scikit-learn.org/stable/modules/cross_validation.html)
	- Splits a data set into multiple parts
		- Then train and test your data on **each part**
		- Then evaluates performance as an average
- [**Classification report**](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.classification_report.html)
	- A built-in report offered by the `sklearn` function `classification_report()`
	- Returns some of the main classification metrics such as precision, recall and f1- score
- [**ROC Curve**](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.roc_score.html)
	- AKA [receiver operating characteristic](https://en.wikipedia.org/wiki/Receiver_operating_characteristic)
	- A plot of true positive rate versus false positive rate
- [**Area Under Curve (AUC) Score**](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.roc_auc_score.html)
	- The area underneath the ROC curve
	- A perfect model achieves an AUC score of 1.0

##### Which classification metric should you use? #####

- **Accuracy** is a good start
	- All classes are balanced
	- That is, similar numbers in all classes
- **Precision** and **recall** become more important when classes are **imbalanced**

| If...                                                     | Then...                  |
| --------------------------------------------------------- | ------------------------ |
| False positive predictions are worse than false negatives | Aim for higher precision |
| False negative predictions are worse than false positives | Aim for higher recall    |
- The **F1-score** is a combination of
	- Precision **and**
	- Recall
- A confusion matrix is always a good way to visualize how a classification model is going

#### Regression Model Evaluation Metrics/Techniques ####

- [**R^2 (pronounced r-squared) or the coefficient of determination**](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.r2_score.html) 
	- Compares your model's predictions to the **mean of the targets**
	- Range: ($-\infty$, 1)
		- $-\infty$ is a very poor model
	- A model that simply predicts the **mean of the targets** has an ${R}^2$ score of 0.
	- A model perfectly predicting the **targets** has an ${R}^2$ score of 1
- [**Mean absolute error (MAE)**](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.mean_absolute_error.html)
	- The average of the **absolute differences** between predictions and actual values
	- Provides an idea of how wrong your predictions actually are
- [**Mean squared error (MSE)**](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.mean_squared_error.html)
	- Average **squared difference** between predictions  and actual values
	- No negative errors
	- Amplifies outliers

##### Which regression metric should you use? #####

- **R^2** is **similar to accuracy**
	- Gives a quick indication of how well your model might be doing
	- Closer ${R}^2$ value is to 1.0, the better the model
	- **Does not** tell you 
		- Exactly how wrong|ijG your model is 
		- In terms of how far off each prediction is
- **MAE**
	- Gives a better indication of how far off each of your model's predictions **on average**
- **MAE or MSE**
	- MSE **amplifies larger differences**


| Pay more attention to... | When being $10k off is ... as bad as being $5k off |
| ------------------------ | -------------------------------------------------- |
| MAE                      | Twice                                              |
| MSE                      | More than twice                                    |
For more resources on evaluating a machine learning model. check out:
- [Scikit-Learn documentation for metrics and scoring (quantifying the quality of predictions)](https://scikit-learn.org/stable/modules/model_evaluation.html)
- [Beyond Accuracy: Precision and Recall by Will Koehrsen](https://towardsdatascience.com/beyond-accuracy-precision-and-recall-3da06bea9f6c)
- [Stack Overflow answer describing MSE (mean squared error) and RSME (root mean squared error)](https://stackoverflow.com/a/37861832)
