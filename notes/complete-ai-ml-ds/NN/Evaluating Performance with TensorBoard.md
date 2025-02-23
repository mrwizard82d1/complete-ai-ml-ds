We've trained our first model
- A good idea is now to **evaluate** the training

Since we included a logging callback
- We can look at these logs using TensorBoard
```
%tensorboard --logdir ./logs
```

Looking at the `epoch_accuracy` graph
- We see that our training data approaches 1 "quickly"
- But our validation data **does not**
- We see similar results for the `epoch_loss` graph

The graphs produced by `%tensorboard --logdir ./logs`
- Allow us to see changes over time
- That is, tracking our experiments **over time**

Our next step
- Use our trained model to **make some predictions**
- In the next video
