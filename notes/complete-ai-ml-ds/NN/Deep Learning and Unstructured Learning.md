Again start with our six-step data modeling workflow
- Problem
- Data
- Evaluation
- Features
- Modeling
- Experiments

Our process will change slightly
- We'll be treating `TensorFlow` differently from `scikit-learn`
- We'll be using (2019) cutting edge packages
- We'll be adding Google Colab to our toolkit

What is `TensorFlow`
- A "deep learning" or "numerical computing" library
- Developed internally by Google
	- Now open source
- Upgraded (prior to video coming out) to v2
	- Now at v2.16.1 (as of 2025-02-08)

Uses of `TensorFlow`
- To build deep learning and neural network models
- To gain insight into unstructured data

Unstructured data
- Cannot be stored (typically) in a `DataFrame`
- Examples
	- Photos
	- Audio
	- Natural language text

Why `TensorFlow`
- Write fast learning code in Python (able to run on a GPU)
- Able to access many pre-built deep learning models
- Whole stack: preprocess, model, and deploy
- Originally designed and used in-house by Google
	- Now open sourced

What is a GPU?
- Graphical processing unit
	- Much faster than CPU for performing numerical computing
- Can find patterns more quickly

Choosing a model (throwback)
- Structured data
	- Use `CatBoost`, `XGBoost` or `RandomForest`
- Unstructured data
	- Create a different kind of model
	- Use `TensorFlow` for support
	- Supports transfer learning

What is _deep learning_?
- Another form of machine learning

What are _neural networks_?
- A type of machine learning algorithm or model
- Used in _deep learning_
- Has
	- Some kind of input
	- Machine learning model
	- Some kind of output
- What are the _nodes_?
	- A smaller model that contributes to the overall model
	- For matching pattern

Where does "deep" come from?
- A neural network uses multiple layers
- Deep learning uses **many and multiple, neural networks**

What kinds of deep learning problems exist?
- Classification
	- Dog breeds in an image
	- Spam or not spam
- Sequence to sequence (`seq2seq`)
	- Siri
	- Google Home
	- Google Translate
- Object detection
	- Similar to image detection
	- But trying to find an object in an image
- Many more

What is _transfer learning_?
- Taking what you know in one domain and applying it to a **different domain**
	- For example, 
		- Have already trained model on dogs
		- Start with that model and apply to birds (or something else)
- Starting from scratch is **expensive** and **time consuming**
- Leverages what is already available

What will we cover?
- Similar work flow to our `scikit-learn` workflow
- Steps are similar; details differ
	- Get data ready
		- Turn data into tensors
	- Pick a model suitable Fit model to our problem
		- Use "TensorFlow Hub"
	- Fit model to data and make a prediction
	- Evaluate the model
	- Improve through experimentation
	- Save and reload trained model

Our "course" approach
- An end-to-end multi-class classification workflow with TensorFlow
- Preprocessing image data
	- Converting data into tensors
- Choosing a deep learning model
- Fitting a model to the data
	- That is, learning patterns
- Making predictions with a model
	- **Using** learned patterns
- Evaluating model predictions
- Saving and loading models
- Using a trained model to make predictions on custom data

The problem we will work on
- The Kaggle dog breed identification problem
	- Determine the breed of a dog in an image
- Multi-class classification

Classification
- "Is this example one thing or another?"
- Binary classification - **two** options
	- For example, spam or not spam
- Multi-class classification
	- **More than** two options
	- For example, dog/cat/bird breeds

Where to get help?
- Follow along with the code
- Try it for yourself
- Press Shift + Cmd + Space to read docstring
- Try again
- Ask (don't forget the Discord chat)

Let's go find those "doggos"!

See [this article from late 2024 comparing PyTorch, Keras, and TensorFlow](https://www.analytixlabs.co.in/blog/pytorch-vs-tensorflow/#PyTorch_vs_TensorFlow)
