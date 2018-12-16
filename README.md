### Multivariate TimeSeries using Recurrent Neural Network - Long Short-Term Memory (LSTM)  

#### Overview

Time series forecasting is essential for many business domains, such as finance and e-commerce platform. Traditionally, these businesses analyze and predict stock price and sales based on historical data using a single time-dependent variable. In the real-word, there are several variables that could lead to data volatility causing forecast instability.

In this use case, I applied Multivariate time series to two time-dependent variables. I used the SP500 closing price and Volatility Index (VIX) with Long Short-Term Memory (LSTM) recurrent neural networks.

 

#### Environment

* Python 3.6
* Keras is installed with the Tensorflow backend

 

#### Dataset

The daily SP500 and VIX data are downloaded from here. These two datasets can be combined using Pyhton Pandas library or any other tools. I did not include that in this use case.

 

#### Data preparation:

* Convert dataset to supervise learning problem: the time series data is a sequence of number that are ordered by date or time index. For supervised learning algorithm, we need to convert the time series data into input pattern (X) and output pattern (y). The Python shift() function is used here to create multivariate input variables (X: SP500_close, SP500_volume, VIX_close) and one output variable (SP500_close at the current date).

* Normalize the input variables: the MinMaxScaler(0 function is used to normailize the features

 

#### Define Model:

* Split the dataset into 80% training and 20% testing sets.
* Define LSTM model with 50 neurons in the first layer and 1 neuron in the output layer.
* Compile model using mean absolute error (mae) as loss function and “Adam” optimized. The Adam optimizer is an extension to stochastic gradient descent, which updates the weights iterative based on training data. Here is the link for more information of how Adam optimized work. I used the recommended default setting by Keras library (lr=0.001, beta_1=0.9, beta_2=0.999, epsilon=1e-08, decay=0.0).


 

#### Fit and Evaluate Model:

* For fitting the model, I used 200 training epochs with a batch size of 30.
* The values for training and testing loss is stored for each epoch iteration by setting  the parameter validation_data to true
* Finally, it plots the training and testing loss.
