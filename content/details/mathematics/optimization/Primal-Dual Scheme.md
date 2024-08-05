* The **primal** is the original form of a [[Linear Programming|linear program]]. It is of the form
  
  $$
    \begin{split}
    \text{optimize } & \ \ \ \ \ c^Tx \\  
    \text{subject to} & \ \ \ \ \ Ax \le b \\ 
    & \ \ \ \ \ x \ge 0 
    \end{split} 
    $$

* The **dual** is another LP derived from the original. The objective is inversed (i.e., if the primal maximizes, the dual minimizes)
  
    $$
    \begin{split}
    \text{optimize } & \ \ \ \ \ b^Ty \\  
    \text{subject to} & \ \ \ \ \ A^Ty \le c \\ 
    & \ \ \ \ \ y \ge 0 
    \end{split} 
    $$
    
    *That is, the constraints become variables and the variables become constraints*.
	* The above is the **symmetric form** of the dual.
	* The **asymmetric form** is one where we get rid of the non-negativity constraints. That is
	  
	  $$
	  \begin{split}
	  \text{optimize } & \ \ \ \ \ b^Ty \\  
	  \text{subject to} & \ \ \ \ \ A^Ty \le c \\  
	  \end{split} 
	  $$
	  
# Theorems
* The **weak duality theorem** states that the objective value of the dual LP at any feasible solution is bound on the objective of the primal LP at any feasible solution.  More formally if the primal LP has a maximization objective [^weak_duality]
  
  $$
  \max_x  c^Tx \le \min_y b^T y
  $$
* The **strong duality theorem** states that *the optima of the primal, if it exists, is equal to the optima of the dual*. That is, for a maximization objective
  
  $$
  \max_x c^T x = \min_y b^Ty
  $$

* Consider a linear program in [[Simplex Method|canonical form]] with an optimal basic feasible solution corresponding to the basis $B$. The vector $y^T=c^T_B B^{-1}$ is an optimal solution to the dual 



[^weak_duality]: See Luenberger and Ye 4.2 for the proof.


# Complementary Slack Theory
* *Intuition*: If we interpret the primal as a resource allocation problem, the dual LP is a resource valuation problem. It has [[Scarcity, Supply, and Demand|similarities to pricing for supply and demand]]
	* *On the consumer side, we have the primal problem*. We want to mix good $i$  dictated by the $x_i$'s . The value of the mixing of these goods is governed by their marginal prices $c_i$.  The constraints are determined by the material available, the $b_i$, and the amount of each material to produce each good ($A$). The constraint is stated as $Ax \le b$ as we have constraints on the raw materials. The consumer's goal is to maximize profit.
	* *On the producer side, we have the dual problem*. We control the price of one unit of each material $y$. Each good that can be made derives from these materials and the relation is captured by $A^T$. It should be the case that $A^Ty \ge c$ since otherwise, the producer can just produce and sell the goods directly. $b$ dictates the overall target level of manufactured raw material. The producer's goal is to minimize the production cost 

* Consider the linear program
    $$
  \begin{split}
  \text{minimize } & \ \ \ \ \ c^Tx \\  
  \text{subject to} & \ \ \ \ \ Ax \le b \\ 
  & \ \ \ \ \ x \ge 0 
  \end{split} 
  $$
  
  Let $B$ be the optimal basis with solution $(x_B,0)$, where $x_B = B^{-1}b$. The corresponding dual solution is $y^T = c^T_B B^{-1}$ 
  
  If we [[Perturbation Theory|perturb]] $b$ by $\Delta b$, the solution becomes $x = (x_B + \Delta x_B, 0)$. The corresponding increment in the cost function is called the **sensitivity** which is calculated as 
  
  $$
  \Delta z = c_B^T \Delta x_B = y^T \Delta b
  $$

 * *The sensitivity of the optimal cost to small changes in the constraints is given by the solution of the dual*.

* The **Complementary Slack Theorem of the Symmetric Form** states the following:  $a_i$ is the $i$-th column of $A$. Let $x$ and $y$ be feasible solutions for the primal and dual. A necessary and sufficient condition that they both be optimal is that $\forall i$
	* $x_i >0 \implies a_i^T y = c_i$
	* $a_j^Ty^ < c_j \implies x_i = 0$. 

* The **Complementary Slack Theorem of the Asymmetric Form** states the following: $a_i$ is the $i$-th column and $a^j$ is the $j$-th row of $A$. Let $x$ and $y$ be feasible solutions for the primal and dual. A necessary and sufficient condition that they both be optimal is that $\forall i$
	* $x_i > 0 \implies a_i^T y=c_i$
	* $y_j > 0 \implies a^j x = b_j$
	* $a_i^T y < c_i \implies x_i = 0$
	* $a^jx > b_j\implies y_j =0$ 
* Another way to say the Complementary Slack Theorem is that:
	* If a dual variable is greater than $0$ (slack), then the corresponding primal constraint must be an equality (tight).
	* If a primal variable is greater than $0$ (slack), then the corresponding dual constraint must be an equality (tight).
	* *Variables in one problem are complementary to constraints in another*
	* A constraint is **slack** if the slack variable is positive.  A variable constrained to be non-negative has slack if it is positive. *There cannot be slack in both a constraint and the associated dual variable*
# Links
* [[Linear and Nonlinear Programming by Luenberger and Ye]] - Ch. 4