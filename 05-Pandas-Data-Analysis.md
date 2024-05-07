## Pandas introduction

- Why pandas?
	- Simple
	- Integrated with many DS and ML Python tools
	- Helps get data ready for ML
- What will we cover?
	- Not everything 
	- Most useful functions
	- Pandas data types
	- Import / export
	- Describing data
	- View / select data
	- Manipulating data
- Where to get help?
	- Follow along with code in Jupyter notebook
	- Try it for yourself
	- If errors, **search**
		- StackOverflow
		- Pandas documentation
	- Try, try again
	- Ask

## Series, data frames and CSVs

- Practice, practice, practice
- `conda env list` to list available `conda` environments
- `pandas` supports loading files
	- From the file system
		- `heart_disease = pd.read_csv("data/heart-disease.csv")`
	- From a URL (the internet)
		- `heart_disease = pd.read_csv("https://raw.githubusercontent.com/mrdbourke/zero-to-mastery-ml/master/data/heart-disease.csv")`
		- Further note the use of the URL for the "raw" format of GitHub

## Describing data with pandas

* `dtypes` 
	: Return the datatypes of all columns (as a `Series`)
- `columns`
	: Returns the names of all the attributes as a `List`
- `index
	: The index (left-most "column") of the data frame
- `describe()`
	: Describes the columns of each data frame
	- Beware of columns of `dtype` `object`
- `info()`
	: A "combination" of `index` and `dtypes` plus some additional information
- `mean()`
	: The mean of all *numeric* columns
- `sum()`
	: Apply the `sum()` function to each column
	- One can also call `sum()` on a **single column**
	- For example, `car_sales['Doors'].sum()`
- `len()`
	: Return the number of rows in a data frame
	