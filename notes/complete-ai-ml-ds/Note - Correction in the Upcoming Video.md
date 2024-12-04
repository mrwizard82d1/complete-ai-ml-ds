The next video contains techniques to
- Deal with missing data
- Turning categorical (non-numerical) data into numbers using Scikit-Learn

Although the video code is correct, there is one improvement which should be noted
- The video shows filling and transforming **the entire data set**
- The code works and runs, however, 
	- It is best to fill and transform training and test sets separately
- The code is "fixed" in GitHub:
	- [introduction-to-scikit-learn.ipynb](https://github.com/mrdbourke/zero-to-mastery-ml/blob/master/section-2-data-science-and-ml-tools/introduction-to-scikit-learn.ipynb)
	- [introduction-to-scikit-learn-video.ipynb](https://github.com/mrdbourke/zero-to-mastery-ml/blob/master/section-2-data-science-and-ml-tools/introduction-to-scikit-learn-video.ipynb)
	- [Full example in Google Colab (this will work straight away)](https://colab.research.google.com/drive/162DyoCBFeufMjJI7n4XCiYpdqIdktZw_)

The main takeaways
- Split your data **first**
	- Thereafter, **always** keep your training and test data **separate**
- Fill/transform the training sets and test sets **separately**
