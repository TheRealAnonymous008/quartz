* **Dynamic Programming** is an [[Algorithms|Algorithm]] applied to [[Recurrence Relations|recursive]] problems.
	* It is usually applied to optimization algorithm with **optimal substructure** -- that is, the optimal solution incorporates optimal solutions to related subproblems.  This can be discovered with the following pattern
		* The problem involves making a choice which splits the problem into one or more subproblems.
		* For subproblems, we assume that the choice leads to an optimal solution (regardless of how it is obtained).
		* As a result of the choice, we determine which subproblems are present and thus characterize the subproblem space -- typically we want simpler spaces first. 
		* Show that the solutions to the subproblems used within an optimal solution to the problem must themselves be optimal via cut and paste -- cutting out the non-optimal solution to the subproblem and pasting in the optimal one leads to a better solution. 
	* Because of optimal substructure, *we can decompose the problem into subproblems and solve them independently.* The optimal substructure of a problem varies in:
		* How many subproblems are used for an optimal solution
		* How many choices we have to determine which subproblems to use. 
	* Subproblems exhibit the following properties:
		* *Subproblems are independent*. That is, the solution to one subproblem does not affect the solution of another subproblem of the same problem. 
		* *Subproblems are overlapping*. That is, a naive recursive solution to the problem revisits the same problem repeatedly .
	* Subproblems can be organized using a **subproblem [[Directed Graph|Graph]]** where vertices corresponds to subproblems and all edges are of the form $(x,y)$ where $x$ is a subproblem that requires the solution of subproblem $y$. 

* The general framework follows the following steps
	* Characterize the optimal solution structure
	* Recursively define the value of an optimal solution
	* Compute the value of an optimal solution, typically in bottom up fashion.
	* Construct an optimal solution from computed information. 

* *Dynamic Programming is less about building giant tabulations, and more about doing recurrences smartly*. 

# Performance
* Dynamic Programming prevents us from efficiently redoing work for subproblems that have already been computed.  
	* One approach is through **memoization** or caching all computed solutions to subproblems. *This imposes a [[Trade Offs#Space vs Time Tradeoff|space time tradeoff]]* 
		* If some subproblems need not be solved, then the top down approach is faster than the corresponding bottom-up approach. 
	* Another approach is to use a **bottom-up approach**  where we solve subproblems based on "size" such that we solve smaller subproblems first. Larger problems only depend on smaller subproblems.  *No subproblem is solved until all its dependents are solved*.
		* Typically if all subproblems must be solved at least once, a bottom up approach outperforms the corresponding memoized approach by a constant factor. 

* With the subproblem graph $G=(V,E)$ in mind, typically the run time of a DP approach is given as 
  
  $$
  O(|V| \times T)
  $$
  Where $T$ is the time to solve each subproblem. This is also the number of choices we have per subproblem (on average). 
  
  Typically the time for subproblem $v$ is given by $T(v) \propto \deg{v}$, in which case a DP approach is $O(|V| + |E|)$. 

* If we want something that can be done quickly, a [[Greedy Algorithm]] might be better.

# Specific Problems
* **Longest Common Subsequence Problem**
  
  Given two sequences $X=(x_1,\dots, x_m)$ and $Y=(y_1,\dots,y_n)$, we wish to find the maximum-length subsequence of $X$ and $Y$
  
  A subsequence of $X$ is defined as a sequence $S=(x_{i_1}, \dots, x_{i_k})$ where $i_1 <i_2<\dots<i_k\le |X|$ are indices. 

* **Optimal Binary Search [[Tree-Based Data Structures|Tree]]**
  
  Given a sequence $K=(k_1,k_2,\dots, k_n)$ of $n$ distinct keys in sorted order, a  set  $D=(d_0,\dots,d_n)$ dummy keys such that 
  
  $d_0$ represents all values less than $k_1$
  $d_i$, for $1\le i \le n$ represents all values between $k_{i-1}, k_{i}$
  
  And a probability distribution associated with each key and dummy key which indicates the probability of them being queried
  
  Find the binary tree which minimizes the expected search cost in the tree $T$. 
  
  $$
  \mathbb{E}[\text{search cost of }T] = \sum_{i=1}^n (\text{depth}_T(k_i) + 1) \cdot P(k_i) + \sum_{i=0}^n \text{depth}_T(d_i) \cdot P(d_i)
  $$

* **Edit Distance Problem**
  
  Let $x[1\dots m]$ be a string we wish to transform to a target string $y[1\dots n]$. Find the least number of transformations needed.
  
  The transformations allowed are chosen from the following. Let $z$ be a working array that is initialized as empty, and which, by the end of the algorithm, is made so that $\forall i: z[i]= y[i]$
  
  Throughout the process we maintain an index $i$ for $x$ and $j$ for $z$. 
	* *Copy* a character so that $z[j]\gets x[i]$, then increment both $i$ and $j$
	* *Replace* a character from $x$ by another character $c$, setting $z[j]\gets c$. 
	* *Delete* a character from $x$ by incrementing $i$. 
	* *Insert* the character $c$ into $z$ by setting $z[j]\gets c$ and incrementing $j$
	* *Twiddle* the next two characters by copying the next two characters in reverse order so that
	  
	  $$
	  \begin{split}
	  z[j] &\gets x[i+ 1] \\
	  z[j+1] &\gets x[i] \\
	  i & \gets i + 2 \\
	  j & \gets j + 2 \\ 
	  \end{split}
	  $$
	* *Kill* the remainder of $x$ by setting $i=m+1$. It must be the final operation if performed. 

# Links
* [[Introduction to Algorithms by Cormen, Leiserson, Rivest, and Stein|CLRS]] - Ch. 15