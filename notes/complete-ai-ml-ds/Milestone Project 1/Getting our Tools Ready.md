We updated our "data dictionary" to prepare
- Result of reading
- We've worked through steps 1-4 
	 - But only in thought

Let's prepare our tools for data analysis and manipulation
- `numpy`
- `matplotlib`
- `pandas`
- Common to import all tools at once
- Import models from Scikit-Learn
	- `LogisticRegression`
	- `KNearestNeighbors`
	- `RandomForestClassifier`
- Import model evaluations from Scikit-Learn
	- From `model_selection`
		- `train_test_split`
		- `cross_val_score`
		- `RandomizedSearchCV`
		- `GridSearchCV`
	- From `metrics`
		- `confusion_matrix`
		- `classification_report`
		- `precision_score`
		- `recall_score`
		- `f1_score`
		- `RocCurveDisplay`

Now that we've gotten our tools ready, let's start applying them
