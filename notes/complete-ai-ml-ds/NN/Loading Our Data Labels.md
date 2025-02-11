Two warnings one may encounter in Colab
- "Runtime disconnected"
- Drive disconnected
- Remember that the **notebook** will remember we were using a GPU

Now, our workspace is ready
- Took awhile
- But we need tools

Now up to step 1: Getting our data ready
- Turn our data into Tensors

Read our data
```python
labels_csv = pd.read_csv('./data/labels.csv')
```
- View data
- Compare data description with description of data on Kaggle

Once we've read our data, we can view it in multiple ways
```python
labels_csv.describe()
```

```python
labels_csv.head()
```

```python
labels_csv['breed'].value_counts()
```

```python
labels_csv['breed'].value_counts().plot.bar(figsize=(20, 10))
plt.show()
```

```python
labels_csv['breed'].value_counts().mean()
```

```python
# More robust than the `mean` against outliers
labels_csv['breed'].value_counts().median()
```

Notice
- Some breeds have many images
```python
labels_csv['breed'].value_counts()[:5]
```
- But others have relatively few
```python
labels_csv['breed'].value_counts()[-5:]
```
- Google recommends
	- [https://cloud.google.com/vision/automl/object-detection/docs/prepare](https://cloud.google.com/vision/automl/object-detection/docs/prepare)
	- A minimum of **10** images to correctly classify
	- Best is 100 annotations per label

We've now begun with some exploration of our data
- Next video, we'll look at how to get our **training images** into our Colab notebook
