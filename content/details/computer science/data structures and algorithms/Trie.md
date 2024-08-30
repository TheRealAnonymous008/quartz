* A **trie** is a $k$-ary search tree for performing key (often strings) searches within a set
  
  All children of a node have a common prefix associated with their parent node. The root of the tree is associated with the empty string.
	* Key lookup is achieved in $O(k)$ time where $k$ is the maximum key length. 

* A **radix tree** is a compressed trie wherein nodes with only one child get merged with their parents. This reduces the space complexity of storing the tree and time complexity of key search. 
	* This is ideal if keys are static and sparse within the key space.

# Suffix Trees
* A **suffix tree** is a compact trie of all suffixes of a given text as their keys and positions in the text as their values. 
  
  More specifically, the suffix tree for the string $S$ of length $n$ is defined such that the following hold:
	* The tree has exactly $n$ leaves numbered $1$ to $n$.
	* Every internal node except for the root has at least two children.
	* Each edge is labelled with a non-empty substring of $S$
	* No two edges starting out of a node can have string labels beginning with the same character.
	* The string obtained by concatenating string labels found on the path from the root to leaf $i$ spells the suffix $S[i,\dots,n]$ 

* $S$ is typically padded with a special end of string character so that no suffix of $S$ is also the prefix of another.
* Sometimes we may use **suffix links** during construction such that 
	* All internal nodes have a suffix link to another internal node. 
	* If the path from the root to a node, spells $\chi\alpha$ where $\chi$ is a single character and $\alpha$ is a possibly empty string, it has a suffix link to the internal node representing $\alpha$.  
		* (*Farach 1.1*) such a suffix link is guaranteed to exist. For nodes that spell $\chi\alpha$, there is always a node in the suffix tree that spells $\alpha$

* The suffix tree satisfies the following properties. 
	* It allows for a linear time solution to the longest common substring problem.
	* The cost to the time speed ups provided by suffix trees is added space complexity. 

* The suffix tree can be constructed in $O(n)$ time.
	* For general alphabets, assuming each edge is lexicographically sorted, the construction is bound by $\Omega(n\log n)$.  With linear construction, the bound becomes exactly $\Theta(n\log \sigma)$, where $\sigma$ is the number of distinct characters. 

# Links
* [[Trees]]
* [[Labelled Trees]]

* [Optimal Suffix Construction with Large Alphabets by Farach](https://users.cs.utah.edu/~pandey/courses/cs6968/spring23/papers/optsuffixtree.pdf)