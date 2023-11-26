# Learning Variants 
* **Classification** involves identifying the group that an entity belongs in given its features. It has important variants. 
* In **batch learning**, we have access to the features and the labels, which we may use to train a model.  *When we then deploy this model, we no longer retrain or update the model* barring extreme circumstances (and we do updates in batches).

# Distribution Shift
* A **distribution shift** pertains to a problem in making a model wherein the assumption that the [[Random Variables and Probability Distributions|distribution]] of the problem domain being stationary does not hold. 

### Covariate Shift
* **Covariate Shift** - involves a shift in the distribution of the features but not the labeling function. More specifically, $P(y\mid x)$ changes. 
* *It is a natural assumption when we believe $x$ causes $y$*. 

* *Assume:* that each data has a nonzero probability of occurring during training time. 
* We can mitigate as follows. Let $q(x)$ be the source distribution and $p(x)$ the target. By definition $p(y\mid x) = q(y\mid x)$ did not change.
  
  We correct using [[Frequentist Statistics#Empirical Risk Minimization|the risk identity]] but using the a modified Empirical risk instead
  
  Let$$\beta_i=\frac{p(x^{(i)})}{q(x^{(i)})}$$So that the empirical risk becomes $$\frac{1}{n}{\sum_{i=1}^n \ \beta_i \ L\left(f(X^{(i)}, y^{(i)})\right)} $$
  All that is left is to actually estimate the $\beta_i$ term. This will require sampling from both $p(x)$ and $q(x)$. [^cov_shift]
* An alternative to this is to use [[Linear Models#Logistic Regression|logistic regression]] to distinguish between samples from one distribution to another. This means we modify $\beta_i$
  
  $$
  \beta_i=\exp\left(h(x^{(i)}\right)
  $$

### Label Shift 
* In **Label Shift** we assume that the distribution of label changes but not $P(x\mid y)$. 
* *It is a natural assumption when $y$ causes $x$*.

* We can use something similar to how we solved [[#Covariate Shift]] except we have to estimate the target label distribution and the confusion matrix using the validation set (from the same distribution as the training set).
* *Assume*: 
	* We have a classifier that is already accurate on the training distribution. 
	* The target distribution only contains categories we have seen before.
	* We are actually dealing with label shift and nothing else. 
* Perform the following procedure 
1. Obtain the classifier model and obtain the confusion matrix as above.
2. Average all the model's predictions at test time together, yielding mean model outputs $\mu(\hat{y})\in\mathbb{R}^k$ where the $i$-the element is the fraction of total predictions on the test set where our model predicted $i$.
3. Solve for the system of linear equations: $$C \ p(y)=\mu(\hat{y})$$
4. Estimate the distribution $q(y)$ by looking at the source data labels. 
5. Obtain $\beta_i$ as shown above and minimize the empirical risk weighted with $\beta_i$.

[^cov_shift]: This is similar in principle to [[Importance Sampling]]

### Concept Shift 
* **Concept Shift** is a form of distribution shift that arises when the very definition of the labels changes.
* We can mitigate this by gradually updating the Model and making it adapt to any changes in data. We do not need to retrain our models.

* **Internal Covariate Shift** refers to a supposed phenomenon that occurs within very deep models. The inputs of the intermediate layers vary in magnitude and can hamper the convergence of the model.
* **Environment Shift** - happens when a model influences an environment that can also adapt to the actions of the model. 

### Nonstationarity 
* **Non-stationary distributions** are a form of distribution shift where the distribution changes slowly and the model is not adequately updated.

# Generalization 
* Generalization gives counter intuitive results when it comes to deep learning 

* Most deep learning modes can achieve arbitrarily low training error. 
* Further gains in model performance (generalization) can only be obtained by reducing overfitting. 
  
  This follows from (1) since we can make the training error arbitrarily small so minimizing the generalization gap boils down to reducing generalization error.
* Complexity  != Overfitting. See [[#Double Descent]] 
* *We cannot actually explain why a DNN generalizes*.
* Regularization techniques do not improve the performance of the model (although they may help computation). 
* Despite how we have parameters in a neural network, the neural network behaves more like a non-parametric model which perfectly interpolates between the training data. In some sense *DNNs are more dependent on the training data and choice of inductive biases than any hyperparameters*. 

# Double Descent
* **Double Descent** pertains to a phenomenon where a model that is extremely simple (underparameterized) and a model that is extremely complex (overparameterized) will have high error, but a model whose number of parameters is about the same as the number of data points used to train it will have low error. 
* Related to [[Statistical Estimators#Bias-Variance Tradeoff|Bias Variance Tradeoff]]

![[Double Descent.png]]
<figcaption> Double Descent Illustration. Taken from evhub </figcaption>

# Permutation Symmetry
* **Permutation Symmetry** is an issue when it comes to training a neural network. 

* In theory, all the parameters from one layer are indistinguishable from those of another layer. So it is possible to permute these parameters in such a way the order is different but the function is the same. 
  
  So, if we initialized each parameter to have the same value, in forward propagation  they will valuate to the same values, and in backpropagation they will have equal gradients meaning they did not update.
  
  Effectively, *this means that our hidden layer would behave as if it were a single computational unit.*

* *We can mitigate permutation symmetry with proper parameter initialization* A **parameter initialization** procedure determines how we initialize each parameter in the neural network. 

### Xavier Initialization 
* One example of a parameter initialization scheme is **Xavier Initialization**, wherein *we initialize weights from a probability distribution* with mean $0$ and variance $\sigma^2$. 

* Consider the current layer and its previous layer which have been initialized by Xavier Initialization (with $\gamma^2$ as its variance)
  
  Let
  $x_j$ be the inputs (size $n_{\text{in}}$) and 
  $\vec{w}_i$ be the weights of this layer.
  $n_{\text{out}}$ be the number of outputs of this layer.
  
  For simplicity, we will assume a lack of nonlinearities, so that the output $o_i$ is simply: $o_i=\vec{w}_i \cdot x_j$.
  
  We can find the expectation and the variance as:
  
  $$
  E[o_i]=E[\vec{w}_i\cdot x_j] = 0
  $$
  
  $$
  \begin{equation}
  \begin{split}
  \text{Var}[o_i]&=E[o_i^2]-(E[o_i])^2 \\
  &=E[(\text{sq}(\vec{w}_i)\cdot \text{sq}(x_j)]\\ 
  &= n_{\text{in}}\sigma^2\gamma^2
  \end{split}
  \end{equation}
  $$
  We denote $\text{sq}(x)$ to be the function where we square all the components in the vector. 
  
  One way to keep the variance fixed is to set $n_{\text{in}}\sigma^2=1$ but backpropagation  means that we also have to do this for the next layer so we have to have $n_\text{out}\sigma^2=1$, which would be impossible (especially since we don't assume $n_{\text{in}}=n_{\text{out}}$).
  
  We loosen the condition and simply satisfy a mix of the two 
  
  $$
  \frac{1}{2}(n_{\text{in}}+n_{\text{out}})\sigma^2 = 1
  $$
  
  This is the variance that we choose to use for Xavier initialization. For the current layer, sample from a probability distribution where $\mu = 0$ and 
  
  $$
  \sigma^2 = \frac{2}{n_{\text{in}} + n_{\text{out}}}
  $$
  
# Gradients and Learning Rate 

# Links
* [Understanding Double Descent](https://www.lesswrong.com/posts/FRv7ryoqtvSuqBxuT/understanding-deep-double-descent)
* [[Neural Network]]