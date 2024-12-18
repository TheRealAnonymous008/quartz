* Let $A$ be any, not necessarily finite, set of elements $a_i$. We refer to $A$ as an **alphabet**, each of $a_i$ as **letters**, any symbol of the form $a_i^n$, $n\in\mathbb{Z}$ is a **syllable** and a finite string $w$ of syllables concatenated is a **word**. The **empty word** is $1$ which has no syllables. 

* There are two **elementary contractions** that can be done in a word. A **reduced word** is one where no more elementary contractions can be performed. 
	* Replace all occurrences of $a_i^ma_i^n$ to $a_i^{m+n}$.
	* Replace all occurrences of $a_i^0$ with $1$. 

* Let $A$ be an alphabet. The group $F[A]$ called the **free group generated** by $A$ is defined as follows. 
  
  Let $F[A]$ be the set of reduced all reduced words from $A$. 
  The [[Fundamental Constructs of Group Theory|group]] operation is defined by concatenation. That is for $w_1,w_2\in F[A]$ the product $w_1\cdot w_2$ is the reduced form of the word obtained by concatenation.

* If $G$ is a group, with a set $A=\set{a_i}$ of [[Cyclic Group|generators]] and if $G$ is [[Group Isomorphism|isomorphic]] to $F[A]$ under a map $\phi:G\to F[A]$ such that $\phi(a_i)=a_i$ then $G$ is **free on** $A$, each $a_i$ are **free generators** of $G$. A group is **free** if it is free on some nonempty set $A$. That is $G \cong F[A]$.

* (*Fraleigh 39.7*) If a group $G$ is free on $A$ and also on $B$, then $A$ and $B$ have the same number of elements. Any two sets of free generators of a free group have the same cardinality. 
* The **rank** of a group $G$ free on $A$ is $|A|$. 

* (*Fraleigh 39.9*) Two free groups are isomorphic if and only if they have the same rank.
* **Nielsen–Schreier theorem** (*Fraleigh 39.10*) A nontrivial proper [[Subgroup|subgroup]] of a free group is free.

* (*Fraleigh 39.12*) Let $G$ be generated by $A=\set{a_i\mid i\in I}$ and let $G'$ be any group. If $a_i'$ for $i\in I$ are any elements in $G'$, not necessarily distinct, then there is at most one [[Group Homomorphism|homomorphism]] $\phi:G\to G'$ such that $\phi(a_i)=a_i'$. If $G$ is free on $A$ (i.e., $G=F[A]$) , then there is exactly one such homomorphism
  
  *A homomorphism of a group is completely determined if we know its value on each element of a generating set*. 
	* *Proof*: For any $x$, the generator sets imply that: 
	  $$
	  x = \prod_j a_{i_j}^{n_j}
	  $$
	  Now
	  $$
	  \phi(x) = \prod_j \phi(a_{i_j}^{n_j}) = \prod_j (a_{i_j}' )^{n_j }
	  $$
	  So indeed $\phi(x)$ is uniquely determined by the value on each element of a generating set.
	  
	  If $G=F[A]$  then define $\psi : G\to G'$ by 
	  $$
	  \psi (x) = \prod_j (a_{i_j}')^{n_j}
	  $$
	  Since $F[A]$ only has reduced words, no two formal products in $F[A]$ are equal (i.e., $\psi(x)$ is uniquely determined) and clearly $\psi$ is a homomorphism. 
* (*Fraleigh 39.13*) Every group $G$ is a homomorphic image of a free group $G$. 


# Links
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh]]
