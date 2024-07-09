* An **Autoregressive Model** is a model which performs regression on the previous values of a particular input.
  
  More specifically, given a [[Random Variables and Probability Distributions|random variable]] which represents sequential data of the form 
  $$
  \{x_0,x_1,\dots, x_t\}
  $$
  To predict $x_{t+1}$, we use $x_0,\dots,x_t$ as inputs in the regression model.
* A **Latent Autoregressive Model** is an autoregressive model where we maintain a summary $h_t$ of the past observations for given sequential data $x$. 
  
  At the same time, we update $h_t$ along with our prediction $\hat{x}_t$.
  
  The end result is that we can estimate $x_t$ with $\hat{x}_t=P(x_t \ | \ h_t)$ and update of the form
  $$
  h_t=g(h_{t-1}, \ x_{t-1})
  $$

![[Latent Autoregressive Model.png]]
<figcaption> Latent Autoregressive Model. Image taken from Zhang et al. </figcaption>

* One technique we can use is **Windowing** where, rather than using  all of $x_t,\dots, x_1$ as inputs, we simply use $x_t,\dots, x_r$ where $n-\tau$ is the size of the window.
  
  We do this so that our features have the same size. 

# Links
* [[Dive into Deep Learning by Zhang, Lipton, Li and Smola]]
* [[Recurrent Neural Network]]
* [[The Transformer Model]]