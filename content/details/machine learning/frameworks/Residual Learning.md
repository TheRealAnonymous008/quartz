* A **Residual Block** is a kind of block whose output is the sum of the current output with the output of the previous layer and with activations applied later. 

![[Residual Block.png]]
<figcaption> Residual Block. Image taken from Zhang et al. </figcaption>

* The motivation behind residual learning hinges on *adding expressivity by having deeper layers more easily express the identity*.
  
  More formally, let $x$ be the input of the current layer and the desired mapping to be learnt is $f(x)$
  
  Rather than learn $f(x)$, we learn the residual $f(x)-x$.


* This procedure serves as another way to counteract problems with [[Pathologies of Deep Learning|gradients]]
* We introduce an inductive bias that our target function has the form $f(x)=x$
* It enforces a nesting of function classes that the model is capable of learning

![[Residual Learning Nested Function Classes.png]]
<figcaption> Residual Learning Nested Classes. Image taken from Zhang et al. </figcaption>

# Links
* [[Dive into Deep Learning by Zhang, Lipton, Li and Smola]]