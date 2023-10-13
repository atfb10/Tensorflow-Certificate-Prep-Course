# Adam Forestier
### October 3, 2023

Resource Link: [MIT Intro to Deep Learning](https://www.youtube.com/watch?v=njKP3FqW3Sk)

**AI** - any techinique that enables computers to mimic human behavior<br>
**Machine Learning** - ability to learn without being explicitly programmed<br>
**Deep Learning** - extract patterns from data using neural networks<br>

#### Activation Functions
- The purpose of activation functions is to *introduce non-linearities* into the network <br>
- Linear activation functions produce linear decisions no matter the network size, non-linearities allow us to approximate arbitrarily complex functions<br><br>

###### 3 common Activation functions
1. Sigmoid *tf.math.sigmoid(z)*
2. Hyperbolic tangent *tf.math.tanh(z)*
3. Rectified Linear Unit (ReLU) *tf.nn.relu(z)*


###### Perceptron - Single Neuron
*How it works* <br>
1. Take inputs 
2. Apply a dot product with your weights
3. Apply a bias
4. Apply an activation function

*Note*: Beecause all inputs are densely connected to all outputs, these layers are called **Dense Layers**<br>
*Note*: Sequential models in Tensorflow are called as such, because you compose a neural network by adding layers in a sequence

###### Quantifying Loss
- The **loss** of our network measures the cost incurred from incorrect predictions
- **empirical loss** measures the total loss over the entire dataset
- **softmax cross entropy loss** can be used with models that output a probability between 0 and 1
- **Mean Squared Error Loss** used w/ regression models that output continuous real numbers

###### Training Neural Networks
*Goal*: We want to find the network weights that achieve the lowest loss <br>
*Remember*: Loss is a function of the network weights <br>
**Gradient Desent Algorithm**
1. Initialize weights randomly
2. Compute gradient
3. Take small step in opposite direction of gradient
4. Repeat until convergence
5. Return weights

###### Computing Gradients: Backpropogation
*How does a small change in one weight affect the final loss?*

###### Optimization
*Remember* - optimization through gradient descent <br>
**Loss Functions**: How much of a step we should take in the direction of a gradient
- *small learning rate*: converges slowly and gets stuck in false local minima
- *large learning rate*: overshoot & become unstable and diverge
- *stable learning rate*: converges smoothly and avoid local minima<br>

*Question*: How do we select a good learning rate? <br>
1. Try lots of different learning rates and see what works "just right"
2. Design an adaptive learning rate that "adapts" to the landscape<br>

**Adaptive Learning Rates**
- Learning rates are no longer fixed
- Can be made smaller or larger depending on how large the gradient is, how fast learning is happening, size of particular weights, etc.

**Gradient Descent Algorithms**
- SGD *tf.keras.optimizers.SGD*
- Adam *tf.keras.optimizers.Adam*
- Adadelta *tf.keras.optimizers.Adadelta*
- Adagrad *tf.keras.optimizers.Adagrad*
- RMSProp *tf.keras.optimizers.RMSProp*<br>

*Note* - In practice, very computationally expensive to compute gradient descent for each point, instead use "mini-batches" select a certain number of randomly selected points to compute weights for

###### Overfitting
- **Underfitting** Model does not have capacity to fully learn data
- **overfitting** Model is too complex, extra paramters, does not generalize well
<br> How to fix? <br>

**Regularization**<br>
*What is it?* Technique that constrains our optimzation problems to discourage complex models <br>
*Why do we need it?* Improve generalization of our model on unseen data <br><br>

**Regularization 1: Dropout**: During training, randomly set some activations to 0
- Typically 'drop' 50% of activations in layer
- Forces network to not rely on any 1 node
**Regalarization 2: Early Stopping**: Stop training before we have a chance to overfit
- Stop when the the testing data loss begins to diverge from training data loss. I.E. model is performing better and better on training data, but performance on test data decreases 