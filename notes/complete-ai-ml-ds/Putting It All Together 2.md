We've seen h2 combine steps using `Pipeline`
- We can also use our search algorithms in a `Pipeline`
	- `GridSearchCV`
	- `RandomizedSearchCV`

Let's see h2 use `GridSearchCV` with our regression pipeline
- H2 "decipher" the step name
	- `"preprocessor__numeric__imputer__strategy"`
	- Notice the **double underscore** (\_\_) separator
- Track back through `Pipeline`s in our code
	- `preprocessor`
	- `numeric`
- The `numeric` pipeline has
	- A step named "imputer"
	- With a `strategy` of "mean"
- Consequently, `GridSearchCV` with a `Pipeline`
	- Will try the imputers of
		- `mean`
		- `median`

H2 access our **model**
- Specify keys to `pipe_grid` of
	- `"model__n_estimators": [500, 750]`
	- `"model__max_depth": [20, 25]`
	- `"model__max_features": ['sqrt', 'log2']`
	- `"model__min_samples_split": [6, 8]`

The `score` of this search: 0.26
- Almost a two-fold improvement 
- But not as good as the improvement in the video

We've covered **alot of material**
- Congratulations!
- It will take **much practice** to improve or learn this process

The best place to go now
- The `scikit-learn` [documentation User Guide](https://scikit-learn.org/stable/user_guide.html)

We will put all these tools together as we take on our milestone projects
