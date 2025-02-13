Last video
- Loaded `labels.csv`
- Reviewed available data

Good if we could view a data inside the notebook
- One option
```python
from IPython.display import Image

# View a dingo
Image('./data/train/001513dfcb2ffafc82cccf4d8bbaba97.jpg')
```
- Another is from `matplotlib`
	- To be demonstrated later

Getting images and their labels
```python
path_names = [f'./data/train/{file_name}.jpg'
			  for file_name in labels_csv['id]]
```

Check if 
- The number of filenames we have found equals 
- The actual number of image files
```python
if (len([path for path 
		 in Path('./data/train').iterdir()])) == len(path_names):
	print("Got 'em all")
else
	print('Hmm. Some got away.')
```

One more check: `Image(path_names[9000])`
- A `tibetan_mastiff`

We have all the correct filenames
- We now need to get the labels in a format we can use
