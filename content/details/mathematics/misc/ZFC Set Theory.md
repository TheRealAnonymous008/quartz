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