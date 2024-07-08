* An **Autoregressive Model** is a model which performs regression on the previous values of a particular input.
  
  More specifically, given a [[Random Variables and Probability Distributions|random variable]] which represents sequential data of the form 
  $$
  \{x_0,x_1,\dots, x_t\}
  $$
  To predict $x_{t+1}$, we use $x_0,\dots,x_t$ as inputs in the regression model.

* One technique we can use is **Windowing** where, rather than using  all of $x_t,\dots, x_1$ as inputs, we simply use $x_t,\dots, x_r$ where $n-\tau$ is the size of the window.
  
  We do this so that our features have the same size. 

# Links
* [[Dive into Deep Learning by Zhang, Lipton, Li and Smola]]