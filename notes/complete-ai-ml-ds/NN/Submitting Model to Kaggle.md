We have our predictions array
- We must now put it in the Kaggle submission format

Looking at the Kaggle `sample_submission` file, we find 
- It wants our models prediction probabilities in a DataFrame (eventually a '.csv' file) with 
	- An ID column 
	- A column for each dog breed
- See www.kaggle.com/competitions/dog-breed-identification/overview/evaluation

To get the data in this format, we will:
- Create a `pandas` `DataFrame` with
	- An ID column
	- A column for each dog breed
- Add data to the ID column by extracting the test image ID's from their path names
- Add the data (the prediction probabilities) to each of the dog breed columns
- Export the `DataFrame` as a '.csv' file to submit it to Kaggle

Create a pandas `DataFrame` with empty columns
```python
predictions_df = pd.DataFrame(
	columns=['id'] + list(unique_names)
)
```

Add data to the ID column by extracting the test image IDs
```python
preductions_df['id'] = [path.stem for path in test_path_names]
```

Add the prediction probabilities for each dog breed
```python
predictions_df[list(unique_breeds)] = test_predictions
```

Let's now export the `DataFrame` to a '.csv' file
```python
predictions_df.to_csv(
	'full_model_predictions_submission_1_mobilenetV2.css',
	 index=false
.)
```

Go to Kaggle and "upload late submission"
- On initial submission, ignore other submissions
- Focus on lowering the score of **my submissions**

Apply our model to custom images (our original goal)
- in the next video
