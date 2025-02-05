* **Utility** pertains to an abstract measure of an agent's satisfaction given a certain world state.
  
* It can be seen applied in the context of [[Economics]] but also [[Game Theory]] and [[Machine Learning]] as the inverse of [[Loss Function|loss]].

# Utility Functions
* A **Utility Function** is a function that maps a vector (representing the world state) $\mathbb{R}^d$ to a real number $\mathbb{R}$. 

* The **Constant Elasticity of Substitution (CES) Utility** is defined as follows: 
  $$
  u(x) = \left[\sum_{i}\alpha_i x_i^\rho\right]^{\frac{1}{\rho}}
  $$
  Where $\alpha_i$ are parameters for each vector component, and $x$ is the world state vector. 
	* When $\rho=1$, the utility corresponds to the case where goods are perfect [[Elasticity|substitutes]].
	* As $\rho\to\infty$ goods become perfect complements.  
