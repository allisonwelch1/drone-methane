

<h1>Plain English Explanation of Neural Networks</h1>
<h3>For My Own Comprehension</h3>

Say we have a dataset with n number of rows and n number of columns. Each row represents an example, x(i), which is a set of feature (column) values. Each example of n feature values corresponds to a class label, y. The object of machine learning is to develop an algorithm that predicts the class label of an example, y, using the set of feature values in that example.

So to start, there needs to be some value input into the classifier. This input, z, is the sum of weighted feature values. $z = w_1 x_1 + w_2 x_2 + … + w_n x_n + b$ b is the bias unit, which is a constant added to the input. It is typically represented at the beginning of the input function as w0x0, where x0 = 1 and w0 is treated like all other weights.

Now the learning starts. Remember that the vector of feature values (x(i)), is known from the data. The vector of weights is typically initialized to small random numbers—that is, we assign random values to the weights to begin with. Then, you can solve for z. Here, the bias works to shift the input function left or right (negative or postive). 

Z gets fed into an activation function, a. For the most simple classifiers, a could be a step function (non-differentiable) or an identity function (a = z). For more advanced classifiers, the activation function is a differentiable, smooth version of the step function. It could be a sigmoid (aka logistic), where $a=\frac{1}{1+e^{-z}}$ or it could be the ReLu function, $a = max(0, z)$ (i.e., a is 0 until z is positive), etc. Using a differentiable activation funciton allows us to compute gradients.

Then, we define a cost function, which gives us an idea of the difference between the the output of the activation function, a (which is not exactly a class label prediction, but rather a continuous "soft" prediciton—during training it is used to compute gradients, and during prediction it is thresholded to produce a discrete class label), and the actual class label, y. For example, the cost function could be the sum of squared errors, $J(w) = \frac{1}{2}\sum (y - a)^2$. When this function is minimized, the model will become the most accurate.

The cost function is minimized through a process of "gradient descent", which is where the differentiable nature of the activation function comes in handy. The cost function can be visually represented (as a function of the weight vector) by a postive parabola with a minimum, which is also the point where the derivative (the slope of the function) is 0 (For one weight, it looks like a parabola; for multiple weights, it’s a multidimensional surface). At a high level, each weight vector (i.e., the initialized weights and then each iteration of updated weights) is used to compute some cost function value (through first the input function and then the activation function), and partial derivative $\frac{\partial w}{\partial J}$ at that point (w, J(w)) gives us some information about what direction the weights need to be pushed in order to move toward the cost function minimum.

To minimize J(w), we calculate the gradient $\frac{\partial J}{\partial w} = \frac{\partial J}{\partial a} \cdot \frac{\partial a}{\partial z} \cdot \frac{\partial z}{\partial w}$. Each partial deriviatve going back is calculated to find $\frac{\partial w}{\partial J}$. Then, the weights are updated by subtracting $\frac{\partial w}{\partial J}$ multiplied by the learning rate from the current weights. This nudges the weights in the direction of the cost function minimum. The gradient is a vector that tells us which way to move the weights.

After training and during prediction, a is thresholded with a step function to get an actual class label prediction.

The above process is what's happening on an individual "neuron" level. In a neural network, many neurons are combined across multiple layers.
