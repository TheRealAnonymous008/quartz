* The **confidence score** represents the probability that the output of the model is correct.

# Cross-Entropy Loss 
* The **cross entropy loss** takes in a probability vector as input. 
* Let: 
  $\hat{y}$ be the input vector representing an estimate.
  $y$ be a vector representing the ground truth
  $q$ be the number of labels that we have (i.e., the dimension of $y$ and $\hat{y}$).
  
  The function is defined as: 
  $$
  L(y,\hat{y})=-\sum_{i=1}^q{y_i \ {\ln{\hat{y}_i}}}
  $$
### Interpretation
* It derives from [[Information Theory|cross entropy]]. We may see this by noting that the "actual probabilities" are those represented in our label vector $y$ and the "believed probabilities" that of $\hat{y}$.
* The cross entropy loss not only minimizes the model's error, but it also minimizes the Entropy, and by extension the amount of information we need to communicate the correct label. In doing so, we also *minimize the degree of uncertainty that the model has as a result of its predictions.*
### Relation to Softmax
* We get the following equations
  $$
  \begin{equation}
  \begin{split}
  L(y,\hat{y}) & =-\sum_{j=1}^q y_j \ \ln \left(\frac{\exp{x_j}}{\sum_{k=1}^q \exp x_k}\right) \\
  & = \ln \left (\sum_{k=1}^q\exp(x_k)
  \right)-\sum_{k=1}^qy_kx_k
  \end{split}
  \end{equation}
  $$
  Now consider the partial derivative with respect to any $x_j$:
  
  $$
  \frac{\partial}{\partial x_j} L(y,\hat{y})=\text{softmax}(x)_j-y_j
  $$
  
  So the gradient is simply 
  
  $$
  \nabla L(y,\hat{y})=\text{softmax}(x)-y
  $$
  
  Which means *to perform gradient descent, all we need is the difference between the expected and observed probabilities.*
  
  Now take the second derivative. We get $$\frac{\partial^2}{\partial^2 x_j} L(y,\hat{y})=S(x)_j \left(1-S(x)_j\right)$$As it turns out, this is equal to the variance of the Softmax function.

# Links 
* [[Differential Calculus]]