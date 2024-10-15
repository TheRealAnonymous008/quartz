* The goal is to solve continuous problems using numeric approximation. 
* Applying the methods of Numerical Methods requires knowledge on [[Computer Number Formats|binary and computer number formats]]. Note that *imprecisions due to how numbers are stored can cascade to inaccuracies when using numerical methods*.

* The **Machine Precision** is defined as the gap between $1$ and the next floating point number. We denote this with $\varepsilon$. 

* The **approximation error** is defined as the error between the true value and the computed value. We compute it as
  $$
  \epsilon = |\hat{x}-x^\ast|
  $$
  Where $\hat{x}$ is our approximation and $x^\ast$ is the true value.

* The **order** of an iterative approximation method is a number $M$ such that the approximation error at the $k$-th step follows the relation
  $$
  \epsilon_k \le C\cdot  \epsilon_{k-1}^M
  $$
  Where $C$ is a constant.
# Topics
* [[Root Finding Algorithms]]
* [[Numerical Differential Calculus]]
* [[Numerical Integral Calculus]]
* [[Numerical Optimization]]
* [[Numerical Linear Algebra]]
* [[Numerical Differential Equations]]


# Calculus
* Complicated Functions can be modeled from simpler pieces. For example using either a [[Taylor Series]] or a Maclaurin Series

# Links
* [[Numerical Methods -- An Inquiry Based Approach with Python by Sullivan]]

