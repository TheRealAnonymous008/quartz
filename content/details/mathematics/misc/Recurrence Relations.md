* A **recurrence** is an equation that describes a function in terms of its value on smaller inputs. 
* We can solve recurrences using the following approaches
	* **Substitution** - Guess the form of the solution and then use mathematical induction to find the constraints and show the solution works. 
	* **Repertoire Method** [^repertoire] - first find settings of general parameters for which the solution is known
	  
	  Then obtain the general case by combining the special cases. 
	  
		* This method is built upon the possibility of combining two recurrences, which usually comes from using linear combinations.  In particular, let 
		  $$
		  x(n) = f(n) + g(x_{n-1}, x_{n-2},\dots,x_0)
		  $$
		  be a linear recurrence relation.
		  
		  We identify building blocks (functions) of $f(n)$ that can be linearly combined
		  
		  $$
		  f(n) = \sum_{i}\lambda_if_i(n)
		  $$
		  
		  The consider the generalized representation 
		  $$
		  Z_n = a_n+g(Z_{n-1}, \dots, Z_0)
		  $$
		  
		  And solve the simpler recurrences 
		  $$
		  x_n^{(i)} = f_i(n) + g(x_{n-1}, x_{n-2},\dots,x_0)
		  $$
		  The set of $x_n^{(i)}$ forms  the repertoire.
		  
		  We then determine the constants $\lambda_i$ 
		  and deduce the solution for $x_n$
		  
		  $$
		  x_n=\sum_{i}\lambda_ix_n^{(i)} + c_0
		  $$
		  The constant $c_0$ is determined using the initial condition

	* **Recursion Tree Method**. We draw out a recursion tree where each node represents the cost of a single subproblem. We then sum all the costs per level of the tree, and then across all levels to obtain the cost of the whole tree.
	  
	  We typically use this to make an ansatz that can be further refined. 
* **Master Method**. This allows us to solve recurrences of the form
  
  $$
  T(n)=aT(n/b) + f(n)
  $$
  Where $a\ge 1$ and $b>1$ are constants and $f(n)$ is an asymptotically positive function.
  
  *We implicitly assume that the problem is divided into equal subproblems*
  
  $T(n)$ has the following asymptotic bounds [^master] [^master_2]
	* If $f(n)=O(n^{log_ba -\epsilon}), \epsilon >0$ then $T(n)=\Theta(n^{log_ba})$ 
	  
	  If the time to divide is dominated by the time to conquer, then the splitting term does not appear. 
	  
	* If $f(n)=\Theta(n^{log_ba} \log^kn)$, where $k\ge 0$, then $T(n)=\Theta(n^{log_b a} \log^{k+1} n)$
	  
	  If the time to divide is equivalent to the time to conquer, then we have a splitting term 
		* If $k>-1$, then $T(n) =\Theta(n^{\log_ba} \log^{k+1}n)$ 
		* If $k=-1$, then  $T(n)=\Theta(n^{\log_ba} \log\log n)$ 
		* If $k<-1$, then $T(n) = \Theta(n^{\log_ba})$ 

	* If $f(n)=\Omega(n^{log_ba+\epsilon}), \epsilon > 0$ and if $af(n/b)\le cf(n)$ for $c<1$ and sufficiently large $n$ (this additional constraint is the regularity condition), then $T(n)=\Theta(f(n))$.
	  
	  If the time to divide dominates the time to conquer, this doesn't yield anything unless the regularity condition holds.

* The **Akra-Bazzi method** is a generalization of the master theorem that assumes subproblems are divided into equal sizes.
  
  We can apply the method to recurrences of the form
  
  $$
  T(x) = g(x) + \sum_{i=1}^k a_iT(b_ix+h_i(x)) \ \ \ \ \text{for }x \ge x_0
  $$
	* We *assume* the following:
	  
	  There are sufficient base cases provided
	  $a_i$ and $b_i$ are constants $\forall i$  such that $a_i>0$ and $0<b_i<1$. 
	  
	  $|g'(x)|\in O(x^c)$ where $c$ is a constant
	  
	  $|h_i(x)|\in O\left(\frac{x}{(\log x)^2}\right)$  $\forall i$. 
	  
	  $x_0$ is constant
	* The asymptotic behavior of $T(x)$ is found by determining the value of $p$ for which
	  
	  $$
	  \sum_{i=1}^ka_ib_i^p =1
	  $$
	  And
	  $$
	  T(x) \in \Theta \bigg( x^p \bigg(1+ \int_1^x \frac{g(u)}{u^{p+1}} \ du \bigg)\bigg)
	  $$

[^repertoire]: From Concrete Mathematics
[^master]: For a proof, see CLRS Ch. 4.6
[^master_2]: Observe that $a$ denotes the number of subproblems and $b$ denotes the relative problem size. 

# Links
* [[Introduction to Algorithms by Cormen, Leiserson, Rivest, and Stein|Cormen, Leiserson, Rivest, and Stein]]
* [[Concrete Mathematics by Knuth, Graham, and Patashnik|Knuth, Graham and Patashnik]]