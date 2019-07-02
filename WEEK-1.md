# WEEK-1 
## Take Away
 
The diagram for traditional programming had `Rules` and `Data` in, `Answers` came out.
 
THe diagram form machine learning had `Answers and Data` in. `Rules` came out.
 
A `Dense` is a layer of connected neurons.
 
`loss` measures how good the results of model is.
 
 
`optimizer` generates a new and improved model or guess (gradient descent).
 
`convergence` is the process of getting very close to the correct answer.
 
## Deep Neuron Network
 
### imports
 
```python
import tensorflow as tf
from tensorflow import keras
import numpy as np
```
 
### Define and Compile the Neural Network
 
Create a model with only 1 layer, which has 1 neuron, and the input shape to it is just 1 value.
```pyton
model = tf.keras.Sequential([
        keras.layers.Dense(units=1, input_shape=[1])
])
```
Compile the model with `loss` function `MEAN SQUARED ERROR` amd `optimizer` as `SGD`
 
```python
model.compile(optimizer='sgd', loss='mean_squared_error')
```
 
### Providing the Data
```python
xs = np.array([1.0,2.0,3.1,4.2,5.33], dtype=float)
yx = np.array([9.0,8.0,7.0,6.0,5.0], dtype=float)
```
### Train the Neural Network
 
```python
model.fit(xs,ys,epochs=500)
```
 
### Make Prediction
```python
model.predict([10.0])
```
 
