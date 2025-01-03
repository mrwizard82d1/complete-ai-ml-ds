**Note**: the previous video contained a **small error**

 When comparing models, 
 - Be careful to compare models **on the same splits**

in the video, the data for the baseline video
- Was **split differently** than he other videos

This example [on Google Colab](https://colab.research.google.com/drive/1ISey96a5Ag6z2CvVZKVqTKNWRwZbZl0m)
- Compares three different models on the heart disease data set
	- A baseline `RandomForestClassifier` with all default parameters
	- A `RandomForestClassifier` tuned with `RandomizedSearchCV`
	- A `RandomizedForestClassifier` tuned with `GridSearchCV`
- The key
	- **All** models use the same data splits created using 
		- `train_test_split()`
		- `np.random.seed(42)`
