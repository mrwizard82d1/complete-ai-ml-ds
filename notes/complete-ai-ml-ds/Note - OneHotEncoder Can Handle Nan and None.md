In newer versions of `scikit-learn`, that is, 0.23 and beyond, the `OneHotEncoder` class was **upgraded** to handle `None` and `NaN` values
- In the video (timestamp 4:30-4:35)
	- We encounter an `Exception`
		- 'ValueError: Input contains NaN'
	- Expected for earlier versions of `scikit-learn`
- In later code,
	- Check version by running `print(sklearn.__version__)`
	- **No** error occurs

Although no error occurs, **you can keep coding**
- Remember, even though you see **no error**
- The dataset **still has missing values**
- By following along with the video, you'll **fill in** these missing values
