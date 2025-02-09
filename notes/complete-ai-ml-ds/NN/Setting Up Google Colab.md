Quick overview
- Use transfer learning 
- And TensorFlow 2.0 
- To classify dog breeds
- Will finish course with end-to-end multi-class classification project
	- An example project

Choosing a model
- Structured data => choose structured data model
	- Get model into numeric form
- Unstructured data => choose deep learning or transfer learning model
	- Still need to get data into numbers
	- More so, into **tensors**

Steps for a new (machine learning) project
- Install `conda` / `miniconda`
- Start new project
- Create project folder
- Collect data
- Create an environment using `conda`
	- Include `jupyterlab` in environment
	- (Or `notebook`)
- Install required libraries
	- `numpy`
	- `pandas`
	- `matplotlib`
	- `scikit-learn`

Why not Colab at the start?
- Colab great for data science / transfer learning
- Sometimes working on projects that cannot be used with Colab

What will we be working on?
- Go to the Kaggle dog breed identification
- Determine breed of a dog from images
	- Download the data from Kaggle
- 

Create account / environment in Colab
- I chose not to do this
- Instead, I 
	- Created a conda environment, `dog-vision`
	- Installed my packages
		- Utility
		- Typical data analysis packages
		- Scikit-learn package
		- TensorFlow

Verified the installed packages
```python
import cytoolz.curried as ctc

import numpy as np
import matplotlib.pyplot as plt
import pandas as pd

import sklearn as sk

import tensorflow as tf
```
