Reminded that many warnings occur in (older) Jupyter notebooks
- "The default value of n_estimators will change from 10 in version 0.20 to 100 in 0.22"

How to address
- Handle warnings
	- `import warnings`
	- `warnings.filterwarnings("ignore")`
- Perhaps not the best

Another mechanism
- Examine the code at which the warning occurs.

Look at version
- Check `scikit-learn` `documentation
- Execute `sklearn.show_versions()`
	- Prints current version of `scikit-learn`

H2 upgrade package **already** in our `conda` environment
- Using `conda`
- `conda activate <env-name-or-path>`
- `conda list` - to list **currently available packages**
- Search topic "conda manager environment"
	- Navigate to "Update Packages" section
	- Update a specific package
		- `conda update scikit-learn`
Other commands
- `conda search scikit-learn` - returns **all** available versions of `scikit-learn`
- `conda search scikit-learn --info` - prints **more detailed** information
	- For example, the video demonstrated that
		- `scikit-learn` 0.22 requires python >=3.6, < 3.7
		- Daniel's version of Python was **3.5**

Uninstall some dependent packages and re-install with specific version numbers
```bash
conda uninstall scikit-learn python
```
- This removes **many, many** packages
- In this state, our notebook (reloaded) **will not work**
- Rebuild environment
	- `conda install python=3.6.9 scikit-learn=0.22 matplotlib numpy pands jupyter`
	- Takes time
- Verify
	- `conda list scikit-learn`
- Remember that we needed to install an **updated Python version**
	- To install an updated `scikit-learn` package

Remember
- Simply executing `conda update <package>` **may fail**
	- Because of a version constraint

Now ready to adjust environment to address (some) warnings
