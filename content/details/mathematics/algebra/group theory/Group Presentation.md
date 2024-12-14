* Let $A$ be a set and $\set{r_i}\subseteq F[A]$.  Let $R$ be the least [[Normal Group|normal]] subgroup of $F[A]$ containing each $r_i$. An [[Group Isomorphism|isomorphism]] $\phi$ of $F[A]/R$ onto a [[Fundamental Constructs of Group Theory|group]] $G$ is a **presentation** of $G$. 
  
  $A$ and $\set{r_i}$ give a **group presentation** denoted as $\braket{A\mid \set{r_i}}$. The set $A$ is the set of **generators for  the presentation** and each $r_i$ is called a **relator**. Each $r\in R$ is a **consequence** of $\set{r_i}$. 
  
  An equation $r_i=1$ is a **relation**.
  
  A presentation is **finite** if both $A$ and $\set{r_i}$ are finite sets. 

* If $A=\set{x_j}$, then the group with the presentation $\braket{A\mid \set{r_i}}$ can be denoted as $F[\set{x_j}]/R$. 
* Two presentations are **isomorphic** if they give isomorphic groups.

* Group presentations present three [[Decidability|undecidable]] problems:
	* Determining if two presentations are isomorphic
	* Determining if a group given by a presentation is finite, free, abelian, or trivial.
	* The **word problem** -- determine if word $w$ is a consequence of a given set of relations $\set{r_i}$. 

* *Every group has a presentation*. 
	* Follows because every group has a homomorphic image to a free group. For any such mapping $\phi$ we can simply take $\text{Ker}(\phi)$ as $R$. 

* The general idea behind Group Presentations is that *they allow us to make groups that are as similar to a specified [[Free Group|free group]]* as possible subject to certain equations that act as constraints.

# Links
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh]]