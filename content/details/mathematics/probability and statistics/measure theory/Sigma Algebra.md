* For a sequence of sets $A_n\in S$, we define the [[Real Analysis|infimum and supremum]] as follows. 
  $$
  \begin{split}
  \inf_{k\ge n} A_k &= \bigcap_{k=n}^\infty A_k  \\
  \sup_{k \ge n} A_k &= \bigcup_{k=n}^\infty A_k
  \end{split} 
  $$
  The **limit supremum and infimum** are defined as 
  $$
  \begin{split}
  \liminf_{n\to \infty} A_n &= \bigcup_{n=1}^\infty \bigcap_{k=n}^\infty A_k \\
  \limsup_{n\to \infty} A_n &= \bigcap_{n=1}^\infty \bigcup_{k=n}^\infty A_k
  \end{split}
  $$
	* *Intuition*: The limit supremum contains all points $x$ that are in infinitely many of these sets.
	* *Intuition*: The limit infimum contains all points that are in all but finitely many of the sets. 
* If for some sequence $\{B_n\}$ of subsets
  $$
  \limsup_{n\to\infty} B_n = \liminf_{n\to\infty}B_n = B = \lim_{n\to\infty} B_n
  $$
  Then $B$ is the **limit** of $B_nn$ denoted $B_n\to B$

* (*Resnick 1.3.1*) Let $\{A_n\}$ be a sequence of subsets of $\Omega$. We have the following
  $$
  \begin{split}
  \limsup_{n\to \infty} A_n &= \left\{ \omega : \sum_{n=1}^\infty \mathbb{1}_A(\omega) = \infty \right\} = \{\omega : \omega \in A_{n_k} , k= 1,2,\dots\}
  \end{split}
  $$
  For some subsequence $n_k$ depending on $\omega$. We write this as 
  $$
  \limsup_{n\to \infty} A_n =\{A_n \text{ i.o}\}
  $$
  Wee also have
  $$
  \begin{split}
  \liminf_{n\to \infty} A_n &= \{\omega : \omega \in A_n \forall n \text{ except a finite number }\} \\
  &= \{\omega : \sum_{n} \mathbb{1}_{A_n^C} (\omega) < \infty\} \\
  &= \{\omega : \omega \in A_n , \forall n \ge n_0(\omega)\}
  \end{split}
  $$
* The following holds
  $$
  \liminf_{n\to\infty} A_n \subseteq \limsup_{n\to\infty} A_n
  $$
  Using De Morgan's we also get
  $$
  (\liminf_{n\to\infty} A_n)^C = \limsup_{n\to \infty} (A_n^C)
  $$

* A sequence of sets $\{A_n\}$ is **monotone non-decreasing** if $A_1\subseteq A_2 \subseteq \dots$. It is **monotone increasing** if $A_1\supseteq A_2 \supseteq \dots$  . We notate  $A_n \nearrow$ to mean monotone non-decreasing and $A \uparrow$ to mean strictly non-decreasing.  We also use $A_n\searrow$ to mean monotone non-increasing and $A_n \downarrow$ to mean strictly non-increasing  

* (*Resnick 1.4.1*) Suppose $\{A_n\}$ is a monotone sequence of subsets.  Then
  $$
  \begin{split}
  A_n\nearrow &\implies \lim_{n\to\infty} A_n = \bigcup_{n=1}^\infty A_n \\
  A_n\searrow &\implies \lim_{n\to\infty} A_n =\bigcap_{n=1}^\infty A_n
  \end{split}
  $$
  Since for any sequences $B_n$, we have
  $$
  \inf_{k\ge n} B_k \nearrow \text{ and }
  \sup_{k\ge n} B_k \searrow
  $$
  It follows that
  $$
  \begin{split}
  \liminf_{n\to \infty} B_n &= \lim_{n\to\infty} \left(\inf_{k\ge n} B_k\right) \\
  \limsup_{n\to\infty} B_n &= \lim_{n\to\infty} \left(\sup_{k\ge n} B_k\right)
  \end{split} 
  $$

* The indicator function satisfies the following
	* $\mathbb{1}_{\inf_{n\ge k} A_n} = \inf_{n\ge k} \mathbb{1}_{A_n}$
	* $\mathbb{1}_{\sup_{n\ge k} A_n} = \sup_{n\ge k}\mathbb{1}_{A_n}$
	* We have the following inequality
	  $$
	  \mathbb{1}_{\bigcup_n A_n} \le \sum_{n} \mathbb{1}_{A_n}
	  $$
	  If the sequence is mutually disjoint, then equality holds
	* $\mathbb{1}_{\limsup_{n\to\infty} A_n} = \limsup_{n\to\infty}\mathbb{1}_{A_n}$
	* $\mathbb{1}_{\liminf_{n\to\infty} A_n} = \liminf_{n\to\infty}\mathbb{1}_{A_n}$
	* $\mathbb{A \ \triangle \ B} = \mathbb{1}_A + \mathbb{1}_B \text{ mod } 2$

* Let $\Omega$ be a set and $\Sigma\subseteq \mathcal{P}(\Omega)$. Then, $\Sigma$ is a **$\sigma$-algebra** if it satisfies the following properties
	* $\Omega\in \Sigma$ 
	* $A\in \Sigma \implies A^c\in \Sigma$
	* $A_i \in \Sigma\implies \bigcup_{i=1}^\infty A_i \in \Sigma$ 
* By De Morgan's Law, a $\sigma$-algebra is also closed under intersection. In fact, *$\sigma$-algebras are closed under countable union, intersection, and complementation

* (*Resnick Corr.1.6.1*) The intersection of $\sigma$-algebras is a $\sigma$-algebra
* Let $\mathcal{C} \subseteq \mathcal{P}(\Omega)$. The $\sigma$-field **generated** by $\mathcal{C}$ denoted $\sigma(\mathcal{C})$ is a  $\sigma$-algebra satisfy ing
	* $\sigma({\mathcal{C}}) \supseteq \mathcal{C}$ 
	* If $\mathcal{B}'$ is some other $\sigma$-algebra containing $\mathcal{C}$, then $\mathcal{B}'\supseteq \sigma(\mathcal{C})$. Thus $\sigma(\mathcal{C})$ is the **minimal** $\sigma$-algebra over $\mathcal{C}$
* (*Resnick 1.6.1*) Given a class $\mathcal{C}\subseteq \mathcal{P}(\Omega)$, there is a unique minimal $\sigma$-algebra containing $\mathcal{C}$.
	* *Proof*: Let $\aleph$ be the set of $\sigma$-algebras containing $\mathcal{C}$. It is easy to show that $\mathcal{C}\subseteq \mathcal{P}(\Omega) \in \aleph$ so at least one $\sigma$-algebra exists. Then the intersection $\mathcal{B}^\beth= \bigcap_{\mathcal{B}\in\aleph}\mathcal{B}$ is also a $\sigma$-algebra and clearly $\mathcal{C}\subseteq \mathcal{B}^\beth$ so $\mathcal{B}^\beth\subseteq \aleph$. 


* (*Resnick 1.8.1*) Let $\Omega_0\subseteq \Omega$.
	* If $\mathcal{B}$ is a $\sigma$-algebra of subsets of $\Omega$, then $\mathcal{B}_0=\{A\Omega_0 \mid A\in B\}$ is a $\sigma$-algebra of subsets of $\Omega_0$. We denote this as $\mathcal{B}_0=\mathcal{B}\cap \Omega_0$ 
	* If $\mathcal{C}\subseteq \mathcal{P}(\Omega)$ and $\mathcal{B}=\sigma(\mathcal{C})$. Then
	  $$
	  \sigma(\mathcal{C} \cap \Omega_0 ) = \sigma(\mathcal{C}) \cap \Omega_0
	  $$
	* (*Resnick Corr.1.8.1*) If $\Omega_0\in \sigma(\mathcal{C})$ then 
	  $$
	  \sigma(\mathcal{C\cap \Omega_0}) = \{A \mid A\subseteq \Omega_0, A\in \sigma(\mathcal{C})\}
	  $$
* Let $X$ be a [[topology|topological space]] where we have a notion of "open sets". 
  
  Then the **Borel $\sigma$-Algebra** is defined as the $\sigma$-algebra generated by the set of open sets $O\subseteq \mathcal{P}(X)$. 
  $$
  \mathcal{B}(X) = \sigma (O)
  $$
# Links
* [[A Probability Path by Resnick]]
* [[Set Theory]] - The $\sigma$-algebra operates on sets.
* [[Real Analysis]] - $\sigma$-algebra has Real Analysis analogues