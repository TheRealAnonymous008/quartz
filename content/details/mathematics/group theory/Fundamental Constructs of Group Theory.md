* A **group** is defined as a pair $G=(G,\ast)$ consisting of a set $G$ and a binary operation $\ast$ on $G$ such that the following properties hold:
	* There exists an **identity element** $e\in G$ such that $\forall x\in G$ 
	  $$
	  e\ast x=  x\ast e = x
	  $$
		* (*Fraleigh 4.17*) There is only one such identity element. 
	* For all $x\in G$, there exists an **inverse element** $x^{-1}\in G$ such that 
	  $$
	  x\ast x^{-1}=x^{-1}\ast x=e
	  $$
		* (*Fraleigh 4.17*) Every element has only one such inverse element.
	  
	* The binary operation is **associative**. That is $\forall x,y,z\in G$ 
	  $$
	  x\ast (y\ast z)=(x\ast y)\ast z
	  $$
	  
* We can denote the group operation as $+$ or $\times$. The product can be denoted as $a+b$, $a\times b$ or simply $ab$. We also have **exponentiation** which can be denoted as $a^n$ or $na$.
# Group Properties
* The identity element is unique.
* The inverse of each element is unique.
* The **Cancellation Law**. That is $\forall x,y,g\in G$ we have that 

$$
\begin{equation} \begin{split}
y \ast g &= x\ast g \implies y =x \\
g \ast y &= g\ast x \implies y = x 
\end{split}\end{equation}
$$


* **Inverse of Products** 
  $$
  (ab)^{-1}=b^{-1}a^{-1}
  $$
* An element $x\in G$ is **idempotent** if $x\ast x=x$.  (*Fraleigh e4.31*) A group has exactly one idempotent element. 
	* In fact, this idempotent element is $e$. 

* **Multiplication defines a bijection**. Let $g\in G$, then there is a bijection $\lambda_L:G\to G$ that is defined as 
  $$
  \lambda_L(x)=g\ast x
  $$
  Similarly $\lambda_R:G\to G$ that is defined as 
  $$
  \lambda_R(x)=x\ast g
  $$
  
* The following formulation for groups called the **One Sided Axioms** are equivalent to the definition of groups.
	* The binary operation is **associative** 
	* There exists a **left inverse** for each element $x^{-1}_L\in G$ such that 
	  $$
	  x^{-1}_L\ast x=e_L
	  $$
	  
	* There exists a **left identity** $e_L\in G$ such that 
	  $$
	  e_L\ast x=x
	  $$

* The **order of a group** pertains to the number of elements. This is denoted $|G|$.
	* **Lagrange's Theorem on Orders** If $G$ is a finite group, then $\forall x\in G$
	  $$
	  x^{|G|}=e
	  $$
	  
* The **order of a group element** $g\in G$ pertains to the smallest positive integer $n$ such that $g^n=e$ or $\infty$ if no such $n$ exists. We denote this by $\text{ord}(g)$.

# Links
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh]]