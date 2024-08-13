# Definitions
* A subset of $E$ is an **independent set** if it is contained in some basis of the matroid. 
	* An **extension** of an independent set $A$ is an element $x\notin A$ such that $A\cup\{x\}$ is an independent set. 
* The **basis** is a maximal independent set. That is, no proper subset of the basis is contained in any other basis of $M$.

* A subset of $E$ is defined as a **dependent set** if it is not an independent set
* A **cycle** is a minimal dependent set

* The **rank** of a matroid $M$ is the number of elements of any basis. The **rank** of $A\subseteq E$, denoted $r(A)$ is the size of the largest independent set contained in $A$. 
* The **rank function** is a function that maps subsets of $E$ to their rank. It satisfies the following properties
	* For each $A\subseteq E$ 
	  $$
	  0\le r(A)\le|A|
	  $$

	* If $A\subseteq B \subseteq E$, then 
	  $$
	  r(A)\le r(B)
	  $$
	  
	*  For any $A,B\subseteq E$, 
	  $$
	  r(A\cup B)+r(A\cap B)\le r(A)+r(B)
	  $$

* A **loop** of a matroid $M$ with set $E$ is an element $e$ which satisfies the property that 
  $$
  r(\{e\}) = 0
  $$
* Two elements $e,f\in E$ are **parallel** if they satisfy 
  $$
  r(\{e,f\}) = 1
  $$
  and they are not loops.  

* A matroid $M=(E,\mathcal{I})$ is **weighted** if it is associated with a weight function $w$ that assigns weights $w$ to each element $x\in S$ such that 
  
  $$
  \begin{split}
  w(x) &>0  \\ 
  w(A) &= \sum_{x\in A} w(x) & \text{ where } A\subseteq E
  \end{split}
  $$


# Matroid Definitions
* **Basis Definition**: A matroid $M$ consists of a non-empty finite set $E$ and a non-empty collection $\mathcal B$ of subsets of $E$ called the bases satisfying the following properties. 
	* No basis properly contains another basis
	* **Basis Exchange Property**
	  
	  If $B_1$ and $B_2$ are bases and $e\in B_1$, then there is an element $f\in B_2$ such that 
	  
	  $$
	  (B_1-\{e\}) \cup \{f\}
	  $$
	  is also a basis of $M$.  
	  [^basis_exchange]

[^basis_exchange]: A generalization of the [[Linear Combination|basis replacement theorem]]

* **Cycle Definition**: A matroid $M$ consisting of a non-empty finite set $E$ and a collection $C$ of non empty subsets of $E$ called its cycles  satisfying the properties:
	* No cycle properly contains another cycle 
	* If $C_1$ and $C_2$ are distinct cycles each containing an element $e$, then there exists a cycle in $C_1 \cup C_2$ which does not contain $e$.

* **Independent Set Definition***. A matroid $M$ consists of a non-empty finite set $E$ and a non-empty collection $\mathcal{I}$ of subsets of $E$ called the set of independent sets satisfying the following properties
	* **Hereditary Property** Let $I$ be an independent set. Then, $J\subseteq I$ is also an independent set 
	* **Independent Set Exchange Property** - If $A$ and $B$ are independent sets, where $|A|\ge |B|$ then there exists $x\in A-B$ such that $B\cup \{x\}$ is an independent set.  

* **Rank Function Definition**. A matroid consists of a non-empty finite set $E$ and an integer valued function, called the rank function $r$ defined on the power set of $E$.
# Basic Theorems 
* Given a set $E$, where $|E|=n$ there are at most $2^{2^n}$ matroids up to isomorphism. 
* (*Wilson e30.5*) Any two bases of $M$ must have the same number of elements. [^1]

[^1]: Follows from the Basis Exchange Property. 

* (*Wilson 33.4*) Let $M$ be a matroid. Then $M$ contains $k$ disjoint bases if and only if for each subset $A\subseteq E$.
  
  $$
  kr(A)+|E-A|\ge kr(E)
  $$

* (*Wilson 33.5*) Let $M$ be a matroid on $E$. Then $E$ can be expressed as the union of $k$ independent sets if and only if for each subset $A\subseteq E$
  
  $$
  kr(A)\ge |A|
  $$

* (*CLRS Lemma 16.8*) Let $M=(E,\mathcal{I})$ be a matroid. If $x\in E$ is an extension of independent set $A\subseteq E$, then $x$ is also an extension of $\emptyset$. 

# Links 
* [[Introduction To Graph Theory by Wilson]]