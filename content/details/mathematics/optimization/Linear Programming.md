* A **linear program (LP)** is an optimization problem in which we optimize an objective function that is linear in the unknowns, subject to constraints in the form of linear equalities and inequalities.
  
  We write this in [[Matrix]] form as
  $$
  \begin{split}
  \text{optimize } & \ \ \ \ \ c^Tx \\  
  \text{subject to} & \ \ \ \ \ Ax \le b \\ 
  & \ \ \ \ \ x \ge 0 
  \end{split} 
  $$
  Where $x, c\in \mathbb{R}^n$ and $A\in\mathbb{R}^{m\times n}$ and $b\in\mathbb{R}^m$ 
	* The above is the **standard form** of an LP problem. 

* A linear programming problem can be converted into an **augmented form**. This introduces **slack variables** $s\in \mathbb{R}^m$ which replaces inequalities with equalities in the constraints. In block form, The matrix can be expressed as
  
  $$
  \begin{bmatrix}
  1 & -c^T & 0 \\
  0  & A & I \\ 
  \end{bmatrix} 
  
  \begin{bmatrix}
  z \\ x \\ s 
  \end{bmatrix} 
  =
  \begin{bmatrix}
  0 \\ b
  \end{bmatrix} 
  $$
  Where $s\ge 0$, and  $x\ge 0$.
  $z$ is the variable to be optimized. 
  $I\in \mathbb{R}^{m\times m}$ is the identity matrix

	* *Intuition*: A slack variable indicates how much we need to add, for each constraint, so that equality is achieved. That is, if $y_i\ge 0$ , then if the constraint is of the form $a^T x \le b_i$, we can remove the inequality by also solving for $a^Tx + y_i = b_i$,   
	* If an inequality has a constraint of the form $a^Tx \ge b_i$, we can introduce a **surplus variable** $y_i$ to transform it as 
	  $$
	  a^T x -y_i =b_i
	  $$
	  Where $y_i \ge 0$. 

* The constraints define a **feasible region**, which is convex. A **feasible solution** is a solution (i.e., value for $x$) in the feasible region. An LP is **infeasible** if no feasible solution exists.

* The **Fundamental Theorem of Linear Programming**  states the following. 
  
  Consider a linear program. Let $P$ be the feasible region. If $P$ is bounded, and $x^\ast$ is an optimal solution to the problem, $x^\ast$ is either a vertex of $P$ or lies on a face $F\subset P$ of optimal solutions. 
  
	* It can also be stated as follows: *the maxima and minima f a linear function over a convex polygonal feasible region must occur at the region's corners*. 
	* If an extrema occurs at two corners, then it must also occur everywhere on the line segment between them
	* (*Luenberger and Ye 2.4*) Another way to interpret this is by considering a matrix $A'\in\mathbb{R}^{n\times m}$ from the augmented form of the LP. Assume $\text{rank}(A') = m$. We can thus consider a submatrix $B\in\mathbb{R}^{m\times m}$ which is invertible. A solution is **basic** if variables not associated with the columns of $B$ are set to $0$.  Then:
		* If there is a feasible solution, there is a basic feasible solution
		* If there is an optimal feasible solution, there is an optimal basic feasible solution
		* Solving a linear program can be done by searching over basic feasible solutions. There are at most $n \choose m$ such solutions. 

# Topics
* [[Simplex Method]]
* [[Primal-Dual Scheme]]

# Links
* [[Linear and Nonlinear Programming by Luenberger and Ye]]
* [[Linear Algebra]]
* [[Convex Optimization]]