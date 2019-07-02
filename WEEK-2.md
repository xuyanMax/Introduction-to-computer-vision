# WEEK-2

## Take Away

There are 6000 images in `Fashion MNIST` dataset.

Each image looks like 28*28 greyscale.

The number of neurons in the last layer should match the number of classes you are classifying.

Consider the impact of training for more or less epochs? 
- You may get a model with less loss after increasing the epochs. 
- You may also see the loss stop decreasing after certain epochs and even increasing, which is the side effect of `overfitting`. 

## Explore the Data

Train a system to recognize fashion images. The dataset is called Fashion MNIST, linked [here](https://github.com/zalandoresearch/fashion-mnist). 

Images are represented as 28 * 28 array of greyscales, with labels as a number, as making use of number is the fundamental step in avoiding bias.

```python
import tensorflow as tf
mnist = tf.keras.datasets.fashion_mnist
# load data
(training_images, training_lables), (validation_images, validation_labels) = mnist.load_data()

# show images
import matplotlib.pyplot as plt
plt.imshow(traning_images[0])

# normalizing the data before put into the network
training_images = training_images / 255.0
validation_images = validation_images / 255.0
```

### Define, Compile and Train the Neuron Network

```python
model = tf.keras.models.Sequential([
        tf.keras.layers.Flatten(),
        tf.keras.layers.Dense(128, activation=tf.nn.relu),
        tf.keras.layers.Dense(10, activation=tf.nn.softmax)
])

model.compile(optimizer = tf.train.AdamOptimizer(),
                loss = 'sparse_categorical_crossentropy',
                metrics=['accuracy'])
model.fit(training_images, training_label, epochs=500)
```


> Parameters in Model
>> - Sequential: that defines a series of layers in the neural network
>> - Flatten: take the 2d data 28*28 and flatten into 1d data 786 * 1
>> - Dense: add a layer of neurons to network ane each of the layer requires `activation function`
>> - Relu: if x > 0 return x else return 0 -- so it passes values or greater to the next layer in the network
>> - Softmax: takes a set of values and effectively choose the biggest one. 
>> - sigmoid: binary classification 
### Evaluate the Neuron Network

```python
model.evaluate(validation_images, validation_labels)
```

### Make Prediction

```python
# return a list of values (10), representing the probability that this item is each of the 10 classes
classification = model.predict(validation_images[0])
```

### Callbacks

Callbacks helps to stop the training when it hits your desired accuracy or loss and further reduces training waiting time. 

#### Define your Callbacks 
```python
class myCallback(tf.keras.callbacks.Callback):
  def on_epoch_end(self, epoch, logs={}):
    if(logs.get('loss')<0.4):
      print("\nReached 60% accuracy so cancelling training!")
      self.model.stop_training = True
```

#### Call your Callbacks

```python
mycallbacks = myCallback()

model.fit(training_images, training_labels, epochs=5, callbacks=[mycallbacks])
```