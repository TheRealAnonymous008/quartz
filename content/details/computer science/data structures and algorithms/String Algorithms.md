# Farach's Algorithm 
* **Farach's Algorithm** [^Farach_1997] aims to construct a [[Trie#Suffix Trees|Suffix Tree]] for integer alphabets (i.e., an alphabet that scales in $O(n)$ relative to the size of the string so that a string contains potentially many characters). 

* An **integer alphabet** is one that is obtained by first sorting each character in the alphabet by rank and replacing them with their rank.

* The algorithm proceeds as follows:
	* *Construct the odd tree $T_0$. *
		* For $i=1,\dots,n/2$, form pairs $(S[2i-1], S[2i])$ and radix sort them in linear time, remove any duplicates and compute $S'[i]=\text{rank}(S[2i-1],S[2i])$. $S'[i]$ is computable in linear time.
		* Then, recursively compute $T_{S'}$, the suffix tree of $S'$. Any odd suffix $S[2i-1],\dots,S[n]$ is a suffix $S'[i]\dots S'[n/2]$. Any internal node of $T_{S'}$ with length $i$ becomes an internal node of  $T_o$ with length $2i$. Call the new tree $T'$ -- the non-compacted trie containing all odd suffixes.  
		* For all internal nodes $u$, take $u$'s children whose edge start with each character, and introduce a new node between $u$ and these children. 
			* If $u$, in the process of doing this, ends up with no children because all of $u$'s children start with the same symbol, we simply delete $u$.
		* $T_o$  can be built for an $n$-string in time 
		  
		  $$
		  T(n) = T(n/2) + O(n) 
		  $$

	* *Construct the even tree $T_e$ from the odd trie.*
		* The idea is to use a lexicographic traversal of the leaves in the compacted odd trie as well as the length of the longest common prefix of adjacent leaves.
		* The even suffixes consist of a single character followed by an odd suffix. We can get the lexicographic ordering of the leaves of $T_e$ in $O(n)$ time. 
		* The longest common prefix can be calculated as follows for leaves $l_{2i}, l_{2j}$. 
		  
		  $$
		  \text{lcp}(l_{2i}, l_{2j}) = 
		  \begin{cases}
		  \text{lcp}(l_{2i+1},l_{2j+1)} + 1 & \text{if } S[2i] = S[2j] \\
		  0 & \text{otherwise}
		  \end{cases}
		  $$
		* Given the odd tree $T_0$, $T_e$ can be constructed in $O(n)$ time.
	* *Merge the odd and even trees.*
		* We use an oracle to report that two edges are "equal" if they share the same first character. 
		* If the oracle reports two edges as equal we break the longer of the two edges and merge its prefix with the shorter of the two edges.  This produces tree $T_S$.
		* Let $u$ be a node. It is odd if it occurs in $T_o$ and even otherwise. 
		  $L(u)$ be the length of $u$ calculated as the sum of the edge lengths from the path from the root to $u$
		  $l_{2i}$ and $l_{2j-1}$ be descendants such that $u$ is their least common ancestor 
		  $\hat{L}(u)=\text{lcp}(l_{2i}, l_{2j-1})$. 
		  
		  (*Farach 4.1*): $u$ is properly merged in $T_S$ if $L(u)= \hat{L}(u)$
		  
		  We can compute $\hat{L}$ in linear time. In fact (*Farach 4.2*) $\hat{L}(u)$= the depth of the tree. 

		* If $L(u)>\hat{L}(u)$ then we merged too far, we have the following procedure. 
		  
		  Let $u$ be a border node if $\hat{L}(u) < L(u)$. Border nodes can be found in linear time.
		  
		  For each $u$, let $T_o^u$ be the subtree below $u$ and the $T_e^u$ be the tree below $u$. 
		  
		  Create a new node $u'$ and make it a child of $p'(u)$, the parent of $u$ in the merged tree
		  
		  Set $L(u')=L(u)$
		  
		  Hang $T_o^u$ and $T_e^u$ off of $u'$. Order the children of $u'$ lexicographically.

* [^Karkkainen_2003] gives an implementation that uses $2/3$-recursion. Essentially, instead of dividing into even and odd, divide by extracting $T_0$ -- the tree of all suffixes in the $i \not\equiv 0 \ \text{mod } 3$ positions, and then reconstruct the remaining suffix trees.
  
  This algorithm is $o(n\log n)$ time and $o(n)$ space algorithm.

[^Farach_1997]: Farach (1997)  [Optimal Suffix Construction with Large Alphabets](https://users.cs.utah.edu/~pandey/courses/cs6968/spring23/papers/optsuffixtree.pdf)
[^Karkkainen_2003]: Karkkainen and Sanders (2003). [Simple Linear Work Suffix Array Construction](http://www.cs.cmu.edu/~guyb/paralg/papers/KarkkainenSanders03.pdf)


# Links
* [[Data Structures]]
