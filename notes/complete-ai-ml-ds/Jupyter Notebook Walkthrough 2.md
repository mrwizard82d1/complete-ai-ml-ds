 A notebook allows one to interactively enter Python code

Input and output
- Cells labeled like `In[##]` are **input cells**
	- That is, cells in which we, the "programmer" entered a Python expression
- Cells labeled like `Out[nn]` are **output cells**
	- That is, cells where the Python interpreter prints the results of the previous input cell (if any)

Pandas introduction
- Read a `.csv` file by invoking the function `pd.read_csv(...)`
- `df.head` displays the rows of a data frame (`df`)
	- No argument (the default) reads the first **five** rows of the data frame
	- A specific, **numeric** arguments reads that many rows from the **start** (or "head") of the data frame
- `df.target.value_counts()` prints a summary of the count of each value found in the `target` column
- `df.target.value_counts().plot(kind='bar')` displays a bar chart
	- In the video, nothing happens until one imports `matplotlib`
	- Perhaps `jupyter lab` imports `matplotlib` by default (if available)?
- Display an image
	- `![](https://dev.mrdbourke.com/zero-to-mastery-ml/images/ml101-6-step-ml-framework.png)`
		- Displays our six-step framework
- Running **terminal commands**
	- Enter the terminal command, for example, `ls`, in a cell
	- Previously, one executed terminal commands by entering `!ls` in a cell

