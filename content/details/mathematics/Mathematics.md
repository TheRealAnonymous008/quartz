* In learning Mathematics, prioritize understanding the definitions first using examples if needed. Then, understand what the theorems are saying. Finally, understand the proofs on why a theorem should be true (analogous to the [[Reading#Three Pass Approach|three pass approach]])
* [The Ansatz Technique](https://en.wikipedia.org/wiki/Ansatz) pertains to solving a problem using an educated guess or assumption  about the solution which may later be verified to be part of the solution.

* [[Problem Solving]] is applicable to all of mathematics.

# Topics
* [[Abstract Algebra]]
* [[Calculus]]
* [[Game Theory]]
* [[Graph Theory]]
* [[Group Theory]]
* [[Information Theory]]
* [[Linear Algebra]]
* [[Number Theory]]
* [[Probability Theory]]
* [[Queueing Theory]]
* [[Statistics]]
* [[Real Analysis]]
* [[Ring Theory]]
* [[Set Theory]]

# Unfiled Math Objects
* Let $x_1,\dots, x_n$ be a set of real numbers. The **geometric mean** is defined as follows: 
  
  $$
  \left(\prod_{i=1}^na_i\right)^{\frac{1}{n}}=\sqrt[n]{a_1\dots a_n}
  $$


* **Brouwer's Fixed Point Theorem** - If $f(x)$ is a continuous function from the domain $[0,1]$ to itself, then there exists at least one value $x^\ast \in [0,1]$ for which $f(x^\ast)=x^\ast$. 

* **Kakutani's Fixed Point Theorem** - A correspondence $C: X\mapsto X$ has a fixed point $x\in C(x)$ if four conditions are satisfied 
	* $X$ is a non-empty, compact, and convex subset of $\mathbb{R}^n$
	* $C(x)$ is non-empty for all $x$
	* $C(x)$ is [[Convex Optimization|convex]] for all $x$
	* $C$ has a closed graph. 

* A **Bipartite Network Projection** is an operation for simplifying a [[Families of Graphs|Bipartite Graph]]. 
  
  Let $U, V$ be bipartitions of the bipartite graph. Then, its **projection on $U$*** is defined as a graph whose nodes are the same as the vertices of $U$, and two nodes are connected if and only if they are linked to the same node in $V$. 
  
  A similar **projection on $V$** can also be defined.
  
  ![[Bipartite Projection.png]]

* For any integer $n$, the following holds
  $$
  \lfloor n/2 \rfloor + \lceil n/2\rceil =n
  $$
  For any integer $x\ge 0$ and integers $a,b>0$
  
  $$
  \begin{split}
  \bigg\lceil \frac{\lceil x/a \rceil}{b} \bigg\rceil &= \bigg\lceil\frac{x}{ab}\bigg\rceil \\ 
  \bigg\lfloor \frac{\lfloor x/a \rfloor}{b} \bigg\rfloor &= \bigg\lfloor\frac{x}{ab}\bigg\rfloor \\ 
  \bigg\lceil \frac{a}{b}\bigg\rceil & \le \frac{a+(b-1)}{b} \\
  \bigg\lfloor \frac{a}{b}\bigg\rfloor & \ge \frac{a-(b-1)}{b} \\
  \end{split}
  $$
# Links

* [Infinite Napkin by Evan Chen](https://venhance.github.io/napkin/Napkin.pdf) - a comprehensive explainer of high level mathematics targeted to a highschooler
* [Jensen's Inequality](https://www.youtube.com/watch?v=u0_X2hX6DWE) - more on the Jensen's Inequality

