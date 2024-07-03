# Reducibility
* A problem $X$ **reduces** to a problem $Y$ if given any input $x$ to $X$, we can construct an input $y$ such that $x$ is a `yes` instance of $X$ if and only if $y$ is a `yes` instance of $Y$. We denote $X\le_p Y$ to say that $X$ reduces to $Y$. 
	* *Intuition*: This can be read as saying solving $Y$ is at least as difficult as solving $X$.

# P and NP
* The set **$\mathcal{P}$** consists of problems that are solvable in polynomial time. 
  
  More formally ,if $n$ is the input size of an instance of the problem, there exists an [[Algorithms|algorithm]] whose runtime can be [[Asymptotic Analysis|asymptotically]] upper bounded by a polynomial function in $n$
\
* The set **$\mathcal{NP}$** is the set of decision problems which are solvable in [[Turing Machine|non-deterministic polynomial time ]]
	* **Non Deterministic Polynomial Time** means that we can guess the answer from polynomially many options in $O(1)$ time
	* More formally, we can define this as follows.
	  
	  A **certificate** is defined as evidence (with polynomial size) that would lead us to establish whether a problem instance is a YES instance.
	  
	  A **certifier** is an algorithm that checks that the certificate is indeed a valid proof.
	  
	  A problem is in **NP** if there exists a certifier that can run in polynomial time.

* $\mathcal{P} \subseteq \mathcal{NP}$ 
	* *Proof*: A polynomial time certifier exists for a problem instance $p\in \mathcal{P}$ -- the polynomial time algorithm itself that can be used to solve $p$.

* Let $X\le_p Y$.
	* If $Y\in \mathcal{P}$ then $X\in \mathcal{P}$ because we can solve $X$ as follows: (1) polytime convert to $Y$, then solve $Y$.
	* If $Y\in \mathcal{NP}$, then $A\in \mathcal{NP}$

* A decision problem $X$ is in  **NP-Hard** if for every problem $Y\in \mathcal{NP}$,  $Y \le _p X$. 
* A decision problem $X$ is said to be **NP-Complete** if 
	* $X\in \mathcal{NP}$
	* For Every problem $Y\in \mathcal{NP}$ $Y\le _p X$

* If a problem is NP-hard then it is at least as difficult to solve as NP.
* Any polynomial time algorithm for $X\in \text{NP-C}$ would give us proof that $\mathcal{P} = \mathcal{NP}$.
* A problem $X$ can be shown to be in NP-C by showing that
	* $X\in \mathcal{NP}$
	* A problem $Y\in \text{NP-C}$ exists such that $Y\le _p X$.  

# Misc
* PPAD is an interesting complexity class. 
# Links
* [P vs NP and the Computational Complexity Zoo](https://www.youtube.com/watch?v=YX40hbAHx3s)
* [Complexity: P, NP, NP-Completeness, Reductions](https://www.youtube.com/watch?v=eHZifpgyH_4)