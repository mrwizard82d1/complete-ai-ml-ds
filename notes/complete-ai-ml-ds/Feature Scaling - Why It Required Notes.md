Rationale
- When range of features differ, many algorithms will "weigh" features with larger magnitudes **more**
	- Probably not wanted

Examples
- k-nearest neighbors
- Principal Component Analysis (PCA)
- Speeds up gradient descent
	- Avoid descending **quickly** on **small ranges**
	- And **more slowly** on **large ranges**

Not so helpful on:
- Tree based model
- Linear Discriminant Analysis (LDA)
- Naive Bayes

Methods of feature scaling
- Prerequisites
	- Import the data
	- Split the data
- Apply feature scaling when trying to **normalize** the data

Min-max scaling
- The `sklearn` package provides a function for min-max scaling

```python
from sklearn.preprocessing import minmax_scale

scaled_data = minmax_scale(original_data)
```
		
- Unclear if this can be used on multiple columns in `pandas`

Mean Normalization
- An alternative to min-max scaling
- Uses the mean of the feature to scale
	
	```python
	from sklearn import preprocessing
	X_train4 = preprocessing.Normalizer()
							.fit(X_train)
							.transform(X_train)
	```
	
- Alternative: use Box-Cox transformation
	
	```python
	from scipy import stats
	
	normalized_data = stats.boxcox(original_data)
	```

Difference between scaling and normalization
- Scaling changes the **range** of data
- Normalization changes the **shape** of the data

Standardization
- AKA _z-score normalization_
- Transforms data to have mean of 0 and standard deviation of 1
- Widely used in
	- SVM (support vector machines)
	- Logistics regression
	- Neural networks
- Using `sklear`

```python
from sklearn.preprocessing import StandardScalar
sc = StandardScaler()
X_train_1 = sc.fit_transform(X_train)
```

Another widely used option is "scaling to unit length"
- Scale the components of a feature vector so that the complete vector has **length one**
	- Typically performed by dividing by the "Euclidean length" of the vector
	- x' = (x / || x ||)
- May use **other norms** in specific situations
	- For example, the L1 norm of the feature vector
		- AKA 
			- _Manhattan Distance_
			- _City-Block Length_ 
			- _Taxicab Geometry_
	- Especially important if, in the following learning steps, the _Scalar Metric_ is used as a distance measure

Conclusion
- "Rule of thumb I following here is any algorithm that computes distances or assumes normality, **scale your features**"
