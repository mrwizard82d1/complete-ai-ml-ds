Once all your data is in numerical format, you probably want to perform one more transformation: "feature scaling."

Two main types:
- Normalization (AKA min-max scaling)
	- Rescales all numerical values to between 0 and 1
		- Lowest value close to 0
		- Highest value close to 1
	- Available in `scikit-learn` class [MinMaxScalar](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.MinMaxScaler.html)
- Standardization
	- Subtracts mean of **all** values from **each** value
		- Consequently, the mean of all features is **zero**
	- Additionally, scales the features to **unit variance**
		- After subtracting, divide each value for the **standard deviation** of the feature
	- `scikit-learn` provides this functionality in the class, [StandardScalar](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.StandardScaler.html)

A couple of notes about **feature scaling**
- Usually **is not** required for target variable
- Usually **not** required for **tree-based models**
	- e.g., Random Forest

Additional resources:
- [Feature Scaling - Why Is It Required](https://rahul-saini.medium.com/feature-scaling-why-it-is-required-8a93df1af310)
- [[Feature Scaling - Why It Required Notes]]
- [Feature Scaling with Scikit-Learn](https://benalexkeen.com/feature-scaling-with-scikit-learn/)
- [Feature Scaling for Machine Learning - Understand the Difference Between Normalization vs. Standardization](https://www.analyticsvidhya.com/blog/2020/04/feature-scaling-machine-learning-normalization-standardization/)

