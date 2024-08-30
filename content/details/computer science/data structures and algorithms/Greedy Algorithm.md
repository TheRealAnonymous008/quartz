* A **greedy algorithm** is one which constructs a globally optimal solution based on a locally optimal choice. 
* *Greedy algorithms do not always give globally optimal solutions*. For this guarantee, we may wish to look at [[Dynamic Programming]] if there are overlapping, independent subproblems. 

* A greedy algorithm is typically created with the following steps.
	* Frame the problem as one where we make a choice and are left with a single subproblem as a result.
	* Prove that there is always an optimal solution the original problem that makes the greedy choice so that the greedy choice is safe.
	* Demonstrate optimal substructure
* For greedy to be applicable, we must satisfy the following properties.
	* The **greedy choice property** means *we can assemble globally optimal solutions by making locally optimal choices*. 
	* **Optimal substructure** --  making the greedy choice leaves us with a subproblem that, combining the optimal solution to that subproblem with the greedy choice, gives us an optimal solution to the original problem. 

* One typical approach to proving a greedy problem's applicability is using a **cut-and-paste** proof.
  
  Argue by contradiction and suppose that an solution does not use the greedy choice.
	* Cut the part that does not use a greedy choice and replace it with one that does.
	* Prove that the new solution gives a more optimal solution, contradicting the previous solution's supposed optimality. 
# Matroids 
* Greedy algorithms apply to [[Matroid Theory|Matroids]] which in turn means that it applies to many problems that involve combinatorial structures that resemble matroids. 
* *Many problems for which a greedy approach provides an optimal solution for can be formulated in terms of finding a maximum-weight independent subset in a weighted matroid*.

* A general greedy approach then gives us the following algorithm for the maximum-weight independent subset problem of a matroid $M=(S,\mathcal{I})$ and weight function $w$

![[Greedy matroid Algorithm.png]]
<figcaption> Greedy Matroid Algorithm from CLRS.</figcaption>

* (*CLRS 16.7, CLRS 16.10, CLRS 16.11*) Show that the greedy algorithm above is correct because Matroids exhibit both the greedy choice and optimal substructure property.
# Links 
* [[Introduction to Algorithms by Cormen, Leiserson, Rivest, and Stein|CLRS]] - Ch. 16