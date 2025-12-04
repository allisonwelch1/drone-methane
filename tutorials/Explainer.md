

<h1>Plain English Explanation of Neural Networks</h1>
<h3>For My Own Comprehension</h3>

Say you have a dataset with n number of rows and n number of columns. Each row represents an example, x(i), which is a set of feature (column) values. Each example of n feature values corresponds to a class label, y. The object of machine learning is to develop an algorithm that predicts the class label of an example, y, using the set of feature values in that example.

So to start, there needs to be some value input into the classifier. This input, z, is the sum of weighted feature values. $z = w_1 x_1 + w_2 x_2 + … + w_n x_n + b$ b is the bias unit, which is a constant added to the input. It is typically represented at the beginning of the input function as w0x0, where x0 = 1 and w0 is treated like all other weights.

Now the learning starts. Remember that the vector of feature values (x(i)), is known from the data. The vector of weights is typically initialized to small random numbers—that is, we assign random values to the weights to begin with. Then, you can solve for z. 

Z gets fed into an activation function, a. For the most simple classifiers, a is an identity function, a = z. For more advanced classifiers, the activation function could be a sigmoid (aka logistic), where $a=\frac{1}{1+e^{-z}}$