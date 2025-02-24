We've seen how to evaluate initial accuracy
- What other ways can we learn about our goal?
- Want to make predictions from a photo

We want to make predictions on the **validation** data
- Remember, we **do not train** on the validation data
```python
predictions = model.predict(
	validation_data,
	verbose=True,
)
```
- We have 200 predictions
	- One prediction for each item in our `validation_data`
- But each prediction contains **120** items
	- One for each possible (unique) dog breed
	- The **index of the maximum** value of a prediction is 
		- The index of the most likely dog breed
- The sum of the values for a single prediction
	- Is approximately 1
	- Because we used the `softmax` evaluation
- Remember
	- Our `softmax` activation transforms 
		- The previous 1280 values 
		- Into an array of 120 values

The predictions are all **numeric**
- We want to transform these numbers back to **dog breeds**
```python
index = 0
print(predictions[0])
print(f'Max value (probability of prediction): {np.max(predictions[0])}')
print(f'Sum: {np.sum(predictions[index])})
print(f'Max index: {np.argmax(predictions[index])}')
print(f'Predicted label: {unique_breeds(np.argmax(predictions[index]))}')
```
- And the result: `border_terrier`

What if we repeat this calculation for a different index?
```python
def summarize_prediction(prediction, index):
	prediction = predictions[index]
	print(prediction)
	print(f'Max value (probability of prediction): {np.max(prediction)})
	print(f'Sum: {np.sum(prediction)})
	print(f'Max index: {np.argmax(prediction)}')
	print(f'Predicted label: {unique_breeds[np.argmax(prediction)]})
```
- And then `summarize_predictions(predictions, 42)` 
	- Predicts 'walker_hound'
	- Probability of prediction: 58%

This is how we convert
- Predictions understood by the computer (numbers)
- To predictions understand by humans (a dog breed)

In the next video, we'll build out the functionality to 
- Compare our predicted label
- To the actual label
