# Analysis
* For algorithms, the input size is usually defined as the amount of [[Information Theory|information]] (i.e. bits) needed to represent the provided inputs in a manner sufficient of the problem. 
* *To simplify analysis, we typically use [[Models of Computation]].*
* We can define an order of growth function for the running time $T(n)$ of an algorithm which gives a simple characterization of the algorithm's efficiency and allows for comparing with other algorithms. This function is dependent on input size.
* We typically make use of [[Asymptotic Analysis]] applied to $T(n)$.

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
* [[String Algorithms]]
* [[Greedy Algorithm]]
* [[Dynamic Programming]]


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
* [[Data Structures]]