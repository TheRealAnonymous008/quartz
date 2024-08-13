* A **Set** is defined as a collection of objects referred to as **elements**. Unless otherwise stated, the elements of a set are distinct.
  
  We denote an element $x$ as being an element of set $X$ using $x\in X$. Otherwise we denote non-membership as, $x\notin X$.
  
  *Notation*: By convention, sets are notated with capital letters.

# Subsets
* A set $A$ is a **subset** of $B$ denoted $A\subseteq B$ if 
  $$
  x\in A \implies x\in B
  $$
  Likewise, we say $B$ is the **superset** of $A$ denoted $B\supseteq A$. 

* Two sets are **equal** denoted $A=B$ if and only if $A\subseteq B$ and $B\subseteq A$. Otherwise, they are **unequal** denoted $A\ne B$
* Two sets are **equivalent** if there exists a bijection that maps each element of $A$ to an element of $B$.
* A **Proper Subset** of $B$ denoted $A\subset B$ is defined so that $A\subseteq B$ and $A\ne B$. 

* The **Power Set** of $S$ denoted $\mathcal{P}(S)$ is defined as the set of all subsets of $S$. 
* The **Universal Set** is the set containing all elements including itself. It is denoted $U$ [^univ_set]
* The **Null Set** is the set containing no elements. It is denoted $\emptyset$

[^univ_set]: Not all formulations of Set Theory allow the formulation of the Universal Set because it gives rise to paradoxes. 


# Sizes of Sets
* The **Cardinality** of a set $A$ denoted $|A|$ refers to the number of elements of the set. 
* The following are true about cardinalitieis
	* $|A| = |B| \iff$ there exists a bijection $f:A\to B$.
	* $|A| < |B| \implies$ there exists an injection and no bijection $f:A\to B$. 
	* $|A| > |B|\implies$ there exists a surjection and no bijection $f:A\to B$. 

* **Cantor's Theorem** Given a set $A$, there is no bijective mapping from $A$ to $\mathcal{P}(A)$. 
  
  *Proof*: 
  Argue by contradiction Suppose such a mapping $f:A\to\mathcal{P}(A)$ exists. Note that the elements of $\mathcal{P}(A)$ are subsets of $A$. It is safe to assume that $f$ is surjective
  
  By construction, consider 
  $$
  B=\{a \ | \ a\notin f(a)\}
  $$
  That is the set of all elements of $A$ which are not elements of their own mapped subset.
  
  Certainly $B\subseteq A$ and $B\in \mathcal{P}(A)$. Now suppose $b\in A, f(b)= B$, which must exist since we have a supposed bijection.
  
  If $b\in B$, then $b\notin f(b)=B$.
  
  Which is a contradiction so our assumption that $f$ was surjective is false, and so there is no bijection from $A$ to $\mathcal{P}(A)$.


* A set is **countable** if there exists a bijection with the elements of the set with any subset of the natural numbers. More formally $|S| \le |\mathbb{N}|$
	* A set is **finite** if it has a bijective mapping to a proper subset of the natural numbers. More formally $|S|<|\mathbb{N}|$. A set that is not finite is **infinite**
	* A set is **countably infinite** if there is a bijective mapping with the set of natural numbers so that  $|S| = |\mathbb{N} |$
* A set is **uncountably infinite** if there is no bijective mapping with the set of natural numbers so that  $|S| > |\mathbb{N}|$

# Set Operations
* For each of the following, let $A$ and $B$ be sets.

* The **Cartesian Product** of $A$ and $B$ is denoted $A\times B$ is defined as the set of all ordered pairs from elements of $A$ with $B$. 
  
  $$
  A\times B=\{(a,b) \mid a\in A, b\in B\}
  $$  
  If we have $A\times A$ we denote it as $A^2$. 
  
  We can chain Cartesian Products to get ordered tuples

* The **intersection** of two sets is defined as 
  
  $$
  A \cap B = \{x\mid x\in A \text{ and } x \in B \}
  $$
  If we have a sequence of sets $A_1,\dots, A_n$ we define this as 
  
  $$
  \bigcap_{i=1}^n A_i
  $$
	* Two sets are **disjoint** if $A\cap B = \emptyset$. 
	* A sequence of sets $A_1,\dots, A_n$ is **pairwise disjoint** if 
	  $$
	  \forall i\ne j, A_i\cap A_j = \emptyset
	  $$
* The **union** of two sets is defined as 
  
  $$
  A \cup B = \{x\mid x\in A \text{ or } x \in B \}
  $$
  If we have a sequence of sets $A_1,\dots, A_n$ we define this as 
  
  $$
  \bigcup_{i=1}^n A_i
  $$

* The **difference** denoted $A-B$ is defined as
  $$
  A-B = \{x \mid x \in A \text{ and } x\notin B\}
  $$

* The **Complement** of set $A$ is denoted $A'$ or $A^C$ and is defined as the set
  $$
  A^C = \{x \mid x\not\in A\}
  $$
  
  If we allow for the Universal Set, an alternative formulation is using
  $$
  A^C = U - A
  $$

## Properties of Set Operations
* For each of these, let $A,B,C$ be sets. The proof for each of these properties follows from properties of the corresponding logical operations 

#### Commutativity
1. $A\cup B=B\cup A$
2. $A\cap B=B\cap A$

#### Associativity
1. $(A\cup B) \cup C= A\cup(B\cup C)$
2. 2.$(A\cap B) \cap C= A\cap(B\cap C)$

#### Distributivity
1. $A\cup(B\cap C)=(A\cup B)\cap (A\cup C)$
2. $A\cap(B\cup C)=(A\cap B)\cup (A\cap C)$

#### Identity
1. $A\cup \emptyset =A$$
2. $A\cap U = A$

#### Complement
1. $A\cup A^C =U$
2. $A\cap A^C=\emptyset$

#### Idempotence
1. $A\cup A=A$
2. $A\cap A = A$

#### Domination
1. $A\cup U=U$
2. $A\cap \emptyset=\emptyset$

#### Absorption
1. $A\cup(A\cap B)=A$
2. $A\cap(A\cup B)=A$

#### De Morgan's Laws
1. $(A\cup B)^C = A^C \cap B^C$
2. $(A\cap B)^C = A^C \cup B^C$

#### Involution
1. ${A^C}^C=A$

#### Complement Laws
1. $U^C = \emptyset$
2. $\emptyset^C=U$

#### Difference Properties
1. $C-(A\cap B)= (C - A)\cup (C -B)$
2. $C-(A\cup B) = (C - A)\cap (C - B)$
3. $C - (B-A) = (A\cap C) \cup (C-B)$ 
4. $(B-A)\cap C = (B\cap C) -A = B\cap (C - A)$
5. $(B-A)\cup C =(B\cup C)-(A-C)$
6. $(B-A)-C=B-(A\cup C)$
7. $A-A=\emptyset$
8. $\emptyset-A = \emptyset$
9. $A-\emptyset = A$
10. $B-A=A^C\cap B$ 
11. $U-A=A^C$
12. $A-U=\emptyset$

# Zermelo-Fraenkel Set Theory + Axiom of Choice
* The **Zermelo-Fraenkel Set Theory with Axiom of Choice** is the most commonly accepted axiomatic schema for Set Theory.
  
  Here, all elements of a set are also treated as sets.

## A1: Axiom of Extensionability
* If every element of the set $x$ is an element of $y$, and every element of the set $y$ is an element of the set $x$, then they are equal. 
  $$
  \forall x\forall y
  \left[
  \left(
  \forall z (z\in x)\iff (z\in y))\implies x=y \right) \right]
  $$
  
* This gives us a formal reason as to why we can compare sets (i.e., we assume that it is possible to do this).

## A2: Axiom of Regularity
* All non-empty sets contain an element that is disjoint with them. 
  $$ 
  \forall x \left( x\ne\emptyset\implies \exists y \left( y\in x\wedge \{y\}\cap x=\emptyset \right) \right) 
  $$
## A3: Axiom Schema of Specification
* A subset for any restriction defined by some predicate formula always exists.

* Let $\phi(x,x_0,\dots,x_{n-1})$ be a pure formula of Axiomatic Set Theory and let $a_0,\dots,a_{n-1}$ be sets. Then for any set $a$, there exists a set $b$ which consists of those elements $c\in a$ for which $\phi(c,a_0,\dots,a_{n-1})$ holds. 
  $$
  \forall x_0,\dots\forall x_{n-1}\forall x\exists y\forall z \left[ z\in y \iff \left ( z\in x \wedge \phi(z,x_0,\dots, x_{n-1}) \right ) \right] 
  $$
  

* Essentially, there is a subset $b$ of $a$ whose members are precisely the members of $a$ that satisfy the formula $\phi$.

## A4: Axiom of Pairing
* If $x,y$ are sets then there exists a set  $z$ which contains $x$ and $y$ as elements. 
  $$
  \forall x \forall y \exists z \left( \left( x\in z \right) \wedge \left ( y\in z \right ) \right)
  $$
  
## A5: Axiom of Union
* The union over the elements of a set exists. 
  $$
  \forall x\exists y\forall z \left[ \left( z\in y \right) \iff \exists t \left( \left( t \in x \right) \wedge \left ( z \in t \right) \right) \right]
  $$

## A6: Axiom of Infinity
* There exists at least one infinite set namely the set containing all Natural Numbers 
  $$
  \exists I(\emptyset\in I \wedge \forall x\in I [(x\cup\{x\})\in U])
  $$
  
## A7: Axiom of Power Set
* The power set of a set exists for all sets 
  $$
  \forall x\exists\mathcal{P}(x)\forall{z}[z\subseteq x\implies z\in \mathcal{P}(x)]
  $$

## A8: Axiom of Choice
* For any set of nonempty sets $x$, there exists a choice function $f$ that is defined on $x$ and which maps each set of $x$ to an element of the set. 
  $$
  \forall{x}[\emptyset\notin x\implies \exists f:x\to\cup x \ \ \forall a\in x(f(a)\in a)]
  $$

* In other words, we can choose one element from each set within a collection of sets. It asserts that such a choice is nonempty, even if the collection is infinite.

# Miscellaneous
* A collection of sets $\mathcal{C}$ is called a **chain** if for each pair of sets in $A,B\in \mathcal{C}$, either $A\subseteq B$ or $B\subseteq A$
* The **Maximal Principle** states the following. Let $\mathcal{F}$ be a family of sets. If for each chain $\mathcal{C}\subseteq F$ there exists a member of $\mathcal{F}$ that contains each member of $\mathcal{C}$, then $\mathcal{F}$ contains a maximal element.

# Links
* [[Relation]]
* [[Boolean Algebra]]