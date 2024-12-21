We just used the Mean Absolute Error (MAE)
- Now we'll look into Mean Squared Error (MSE)

Why MSE?
- Because we square the errors, we
	- "Penalize" (or amplify) predicted values with larger differences from the actual (target) values

Let's see MSE in action
```python
from sklearn.metrics import mean_square_error

y_predictions = model.predictions(X_test)

mse = mean_squared_error(
	y_true=y_test,
	y_pred=y_predictions,
)
mse
```

Hmmm. Why might the MSE be **lower** than MAE?
```python
df['squared diffreneces'] = \
	np.square(df['differences'])
df.head(count=10)
```
- Interesting, we observe that
	- Values between -1 and 1 become **smaller**
	- Values less than -1 or greater than 1 become **larger**

Let's investigate the effect of a single large error
- Change the `squared_difference` for row 0 to 16
- Mean of (large) errors is ~0.2677
- Difference between mean of large errors and MSE is 
	- ~0.0038 (still a **small** error)

Let's investigate the effect of many large errors
- Copy `df_large_error` data frame
- Replace the 'squared_differences' of rows 1-100 with 20
- Now mean of many large errors is ~0.7424
	- Difference with MSE is ~0.4785

Generally
- The MSE is **greater than** MAE
- Another option root mean squared error (RMSE)

A summary of regression metrics:
![[Which Regression metric should you use?.png]]

MAE or MSE: a rule of thumb?
| Pay more attention to... | When... |
| ----------------------- | -------- |
| MAE | Being $10,000 off is **twice** as bad as being $5000 off (linear "badness" |
| MSE | Being $10,000 off is **more than twice** as bad as being $5000 off (above linear "badness") |
