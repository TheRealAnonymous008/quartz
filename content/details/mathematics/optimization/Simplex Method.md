* The idea is built on the Fundamental Theorem of [[Linear Programming]]. *We proceed from one feasible solution of the constraint set in augmented form to another until the optimum is reached.*
* For this, we assume we have a feasible region in the form $Ax = b$, $\forall x_i \ge 0$. 
  
  We also assume that if $A\in \mathbb{R}^{m\times n}$, $x\in \mathbb{R}^n$ and $b\in \mathbb{R}^m$ then $\text{rank}(A) = m$. Otherwise, either $Ax=b$ has redundant solutions that can be dropped or the linear program has no solution.

* In augmented form, we refer to the matrix
  $$
  \begin{bmatrix}
  1 & -c^T & 0 \\
  0 & A& b
  \end{bmatrix}
  $$
  As the **tableau**. If the columns of $A$ can be rearranged so that it contains the identity matrix of order $m$ then the tableau is in **canonical form**. A variable is **basic** if it corresponds to a column of the identity matrix, and **free** otherwise. 
	* The tableau in canonical form may then look like the following, where basic variables are separated from free variables
	  
	   $$
	  \begin{bmatrix}
	  1 & -c^T_B & -c_D^T & 0 \\
	  0 & I &  D& b
	  \end{bmatrix}
	  $$
	* If we set the values of the non-basic variables as $0$. A solution can easily be obtained using methods such as Gaussian elimination. We refer to this as a **basic solution**. 
	  
	  Applying row addition operations and considering $z_B$, the value of the objective function in a basic solution, gives us another tableau in canonical form
	  
	  $$
	  \begin{bmatrix}
	  1 & 0  & -\overline{c_D}^T & z_B \\
	  0 & I &  D& b
	  \end{bmatrix}
	  $$
	  
	  *This follows because the basic variables are linearly independent. The free variables are linear combinations of the basic variables*.

* A **pivot operation** is used to move from a basic feasible solution to another basic feasible solution.  It involves selecting a non-basic column and applying row transformations so that it is a unit vector. It is then used as a replacement column to the Identity Matrix. 
  
  *If we look at the basic variables as defining a [[Linear Combination|basis]], a pivot lets us define a new basis*.  
  
  We refer to the variable used as a new basic variable as the **entering variable** and the variable it replaces as the **leaving variable**
	* *The entering variable is selected to optimize the objective function*
	  
	  Typically, for maximization the choice of entering variable is one whose entry in the first row of the tableau is positive. If there are ties, we may use additional rules. If our goal is minimization, we change the choice to be the negative.
	  
	  If no such choice exists, we in fact have an optimal solution.
		* More formally, for Tableau $1$ (where we have $-c_D^T$) choose column $j$ such that $c_j - z_j > 0$ 
		  
		  For Tableau 2 (where we have $-\overline{c}^T$), choose column $j$ such that $c_j > 0$.
		* We can interpret $z_j$ as the price of a unit of the column $a_j$ when constructed from the current basis. *The difference between the synthetic and direct price of the column determines whether that column should enter the basis*
	* *The leaving variable is selected to maintain feasibility (i.e., the non-negativity constraint)*
		* We only choose from the positive entries since this guarantees the entering variable will be nonnegative.
		* Select the pivot row so that the other basic variables remain positive. This occurs when the value of the entering variable is minimum. Let $c, r$ be the pivot column and row respectively. Choose $r$ such that 
		  
		  $$
		  b_r / a_{rc}
		  $$
		  is the minimum over all $r$ so that $a_{rc}>0$. 
		  
		  If no such $r$ exists, we can stop as the problem is unbounded.

* The Simplex [[Algorithms|algorithm]] then proceeds as follows
	* Construct a tableau corresponding to a basic feasible solution
	* Check if the current basic feasible solution is optimal.
	* Select the entering variable
	* Select the leaving variable.
	* Perform a pivot.

# Links
* [[Linear and Nonlinear Programming by Luenberger and Ye]] - Ch. 3
* [[Linear Algebra]]