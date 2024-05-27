# Analysis
* For algorithms, the input size is usually defined as the amount of [[Information Theory|information]] (i.e. bits) needed to represent the provided inputs in a manner sufficient of the problem. 
* We can define an order of growth function for the running time $T(n)$ of an algorithm which gives a simple characterization of the algorithm's efficiency and allows for comparing with other algorithms. This function is dependent on input size.
* When we are only concerned with the order of growth at large input, we are studying the **asymptotic efficiency**.  [^asymptotic_1] [^asymptotic_2] [^asymptotic_3]
	* For a given function $g(n)$, the **asymptotic tight bound** denoted $\Theta(g(n))$  is defined as
	  
	  $$
	  \Theta(g(n)) = \{f(n) \mid \exists c_1, c_2, n_0 \ \text{ such that} \ \ \ \ \  0 \le c_1\ g(n) \le f(n) \le c_2 \ g(n)  \ \ \forall n\ge n_0\}
	  $$

	* For a given function $g(n)$, the **asymptotic upper bound** denoted $O(g(n))$ is defined as 
	  
	  $$
	  O(g(n)) = \{f(n) \mid \exists c n_0 \ \text{ such that} \ \ \ \ \  0 \le f(n) \le c \ g(n)  \ \ \forall n\ge n_0\}
	  $$
	* For a given function $g(n)$, the **asymptotic lower bound** denoted $\Omega(g(n))$  is defined as
	  
	  $$
	  \Omega(g(n)) = \{f(n) \mid \exists c, n_0 \ \text{ such that} \ \ \ \ \  0 \le c\ g(n) \le f(n)  \ \ \forall n\ge n_0\}
	  $$

	* For a given function $g(n)$, the **strict asymptotic upper bound** denoted $o(g(n))$ is defined as 
	  
	  $$
	  o(g(n)) = \{f(n) \mid \exists c n_0 \ \text{ such that} \ \ \ \ \  0 \le f(n) < c \ g(n)  \ \ \forall n\ge n_0\}
	  $$
	  Here $f(n)$ becomes infinitesimally small relative to $g(n)$ as $n\to \infty$.

	* For a given function $g(n)$, the **strict asymptotic lower bound** denoted $\omega(g(n))$  is defined as
	  
	   $$
	  \Omega(g(n)) = \{f(n) \mid \exists c, n_0 \ \text{ such that} \ \ \ \ \  0 \le c\ g(n) < f(n)  \ \ \forall n \ge n_0\}
	  $$
	  Here $f(n)$ becomes arbitrarily large relative to $g(n)$ as $n\to \infty$.

	* An alternative definition can be formulated by considering $L = \lim_{n\to\infty} \frac{f(n)}{g(n)}$.
		* $f(n) = o(g(n)) \iff L = 0$
		* $f(n) = \omega(g(n)) \iff L = \infty$ 
		* $f(n)=O(g(n)) \iff L \ne \infty$
		* $f(n)= \Omega(g(n)) \iff L \ne 0$ 
		* $f(n) = \Theta(g(n)) \iff L\ne 0, \infty$ 

	* *CLRS 3.1* For any two functions $f(n)$ and $g(n)$ we have that
	  
	  $$
	  f(n)=\Theta(g(n)) \iff f(n) =\Omega(g(n)) \ \wedge \ f(n) = O(g(n)) 
	  $$
	* *The asymptotic functions above define equivalence on the space of functions*

	* Some additional rules
	  $$
	  \begin{split}
	  f=O(g) &\iff g = \Omega(f) \\ 
	  f= o(g) &\iff g = \omega(f) \\ 
	  f = o(g) & \implies f = O(g) \\ 
	  f = \omega(g) &\implies f= \Omega(g) 
	  \end{split}
	  $$

![[Asymptotic Analysis.png]]
<figcaption> Asymptotic Analysis. Image taken from Cormen, Leiserson, Rivest, and Stein </figcaption>

[^asymptotic_1]: These can be used to analyze other functions as well. However, do note that we implicitly assume that for large enough $n$, the function becomes non-negative. 
[^asymptotic_2]: When we say $f(x)=O(g(x))$ we implicitly mean $f(x) \in O(g(x))$. 
[^asymptoic_3]: Another way to read the definitions is that the only way for $g$ to compare to $f$ is if it is scaled by an appropriate constant $c>0$.

* In analyzing algorithms and proving correctness, it is often helpful to observe invariants. 

* The **Divide and Conquer Paradigm** involves solving a problem recursively by applying the following steps at each level of recursion: [^dnc]
	* *Divide* the problem into subproblems that are instances of the larger problem
	* *Conquer* the subproblems by solving them recursively, up until a base case 
	* *Combine* the solutions of the subproblems into the solution for the original problem.
[^dnc]: Divide and Conquer is inherently tied to recurrence relations. In practice, when we use recurrence relations we usually make simplifying assumptions that ignore inconvenient technical details (floors and ceilings)  and boundary conditions. 


* **Randomized Algorithms** are those that apply randomness either to the input or in the process of executing the algorithm itself 
* Randomized algorithms are typically tied to **Probabilistic Analysis** where we operate on the entire distribution of possible inputs
	* When dealing with analysis of Randomized algorithms, we typically assume that all possible inputs are equally likely. 

## List Permutation Algorithms
### Permute By Sorting
![[Permute by Sorting.png]]
<figcaption> Permute by Sorting. Image taken from CLRS</figcaption>


* (*CLRS Lemma 5.4*) Assuming all priorities $P$ are distinct, then the input is randomly permuted. 

### Fisher-Yates 
![[Fisher Yates.png]]
<figcaption> Fisher Yates Algorithm. Image taken from CLRS</figcaption>

* (*CLRS Lemma 5.5*). This algorithm produces a uniform random permutation.
  
  This holds because of the following following loop invariant:
  
  Just prior to the $i$-th iteration of the loop, for each possible $(i-1)$-permutation of the $n$ elements, $\sigma$ the subarray $A[1,\dots,i-1]$ contains $\sigma$ with probability 
  
  $$
  P(\sigma) = \frac{(n-i+1)!}{n!}
  $$


# List of Topics
* [[Sorting Algorithms]]
* [[Greedy Algorithm]]


* [[Algorithms in Games]]
* [[Machine Learning]]
* [[Network Communities#Community Detection Algorithms|Community Detection Algorithms]]

* [Bee Search](https://en.wikipedia.org/wiki/Bees_algorithm)
* [LLL Lattice Reduction Algorithm](https://en.wikipedia.org/wiki/Lenstra–Lenstra–Lovász_lattice_basis_reduction_algorithm)

# Links 
* [[Algorithm Design by Kleinberg and Tardos]]
* [[The Algorithm Design Manual by Skiena]]
* [[Introduction to Algorithms by Cormen, Leiserson, Rivest, and Stein]]

* [[Recurrence Relations]]