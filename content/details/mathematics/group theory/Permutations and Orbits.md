* A **permutation** of a set refers to a bijective mapping from the set to itself. 
* The **orbit** of an element $a$ of a set under the permutation $\sigma$ is the set defined as
  $$
  \mathcal{O}_{a,\sigma} = \{\sigma^k(a) \mid n \in \mathbb{Z}\}
  $$
  It is the set of all possible values that an element can be mapped to using only the permutation. 
	* The orbits of a permutation form an equivalence class.
* A **cycle permutation** is a permutation with at most one orbit containing more than one element.
	* All permutations can be expressed as the product of disjoint cycles.
	* The **length** of a cycle is defined as the number of elements in its largest orbit. 
	* Cycles can be expressed in [Cycle Notation](https://en.wikipedia.org/wiki/Cyclic_permutation)
* A **transposition** is a permutation which involves swapping exactly two elements. 
	* (*Fraleigh 9.15*) All permutations can either be expressed as the product of an even number of transpositions or an odd number of transpositions, but never both.
	* The **parity** of a permutation is **even** if it needs an even number of transpositions and **odd** otherwise .