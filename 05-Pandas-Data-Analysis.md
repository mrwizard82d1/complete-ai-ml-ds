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
- `conda activate <env-name-or-path>` to activate our `conda` environment
- Use `import pandas as pd` to import pandas
- Two main datatypes
	- `Series` : One-dimensional datatype
	- `Dataframe`: Two-dimensional datatype
		- Can be created **from** one or more `Series`
- See the file [[Anatomy of a Data Frame.png]] for basic parts
- `pandas` supports loading files into a data frame (typical usage)
	- From the file system
		- `heart_disease = pd.read_csv("data/heart-disease.csv")`
	- From a URL (the internet)
		- `heart_disease = pd.read_csv("https://raw.githubusercontent.com/mrdbourke/zero-to-mastery-ml/master/data/heart-disease.csv")`
		- Further note the use of the URL for the "raw" format of GitHub
- Additionally, `pandas` supports saving files
	- For example, `car_sales.to_csv('car_sales.csv')` will 
		- Write the data frame, `car_sales`, to disk
		- The written file will contain the data frame data written as a `.csv` file
	- The method, `DataFrame.to_csv()` takes an optional, boolean parameter, `index`
		- If `index` is "truthy," the default, `to_csv` will write the "index" column
		- If `index` is  "falsy", `to_csv` will **not** write the index column
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
	