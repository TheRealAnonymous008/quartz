* A **permutation** of a set refers to a bijective mapping from the set to itself. 
* The **orbit** of an element $a$ of a set $A$  under the permutation $\sigma$ is the set defined as
  $$
  \mathcal{O}_{a,\sigma} = \{\sigma^k(a) \mid n \in \mathbb{Z}\}
  $$
  It is the set of all possible values that an element can be mapped to using only the permutation. 
	* The orbits of a permutation form an [[Relation|equivalence class]]. 
* A **cycle permutation** is a permutation with at most one orbit containing more than one element.
	* (*Fraleigh 9.8*) *All permutations can be expressed as the product of disjoint cycles.* Each cycle corresponds to one orbit and the orbits are disjoint equivalent classes.
	* The **length** of a cycle is defined as the number of elements in its largest orbit. 
	* Cycles can be expressed in [Cycle Notation](https://en.wikipedia.org/wiki/Cyclic_permutation) $(a_1,\dots,a_n)$ where the cycle is understood to take $a_1$ to $a_2$, $a_2$ to $a_3$ and so on, and $a_n$ to $a_1$. Any other element of $A$ not included is understood to be fixed.

* A **transposition** is a permutation which involves swapping exactly two elements. 
	* A transposition is a cycle of length $2$.
	* (*Fraleigh 9.15*) All permutations can either be expressed as the product of an even number of transpositions or an odd number of transpositions, but never both.
		* If we use the corresponding [[Matrix|permutation matrix]], the [[Determinant|determinant]]'s sign remains constant.
	* The **parity** of a permutation is **even** if it needs an even number of transpositions and **odd** otherwise .

# Links
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh]]