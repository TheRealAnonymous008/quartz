* Let $M$ be a matroid on $E$.  The **Dual Matroid** of $M$, denoted $M^\ast$ is defined as the matroid such that 
	* It is also on $E$ 
	* A set in $M^*$ is independent if and only if there exists a basis in $M$ that is disjoint from it.

# Definitions
* $B\subseteq E$ is a **cobasis** of $M$ if they form a basis in $M^\ast$. 
	* (*Wilson 32.2*) If $B$ is a basis of $M$, then $E-B$ is a basis on $M^\ast$. 
	* (*Wilson 32.5*) Every cobasis of a matroid intersects with every cycle. 
		* *Remark*:  This generalizes *Wilson 9.3*.
* $C\subseteq E$ is a **cocycle** of $M$ if they form a cycle in $M^\ast$ 
	* (*Wilson 32.4*) Every cocycle of a matroid intersects every basis. 
		* *Remark*: This generalizes *Wilson 9.3a.z*. 

* The **corank** of $M$ is defined as the rank of $M^\ast$ [^1] 
	* (*Wilson 32.1*) The rank function of the dual $M^*$, denoted $r^*$ may be defined as: 
	  $$
	  r^*(A)=|A|+r(E-A)-r(E)
	  $$
	  Where $A\subseteq E$.


[^1]: It is analogous to the concept of nullity in [[Linear Algebra]].

# Theorems 
* Matroid Duality is involutionary 
  $$
  M^{\ast\ast} = M
  $$
* The graphic and cogrpahic matroids are [[Matroid Duals|duals]].  [^2]


[^2]: This follows from [[Graph Duality#Cycle and Cut-set|here]]. 

* (*Wilson e32.8*) Let $M$ be a matroid. For cycle and cocycle $C,C^*$, we have $$|C\cap C^*|\ne1$$
	* *Proof*: 
	  Let $C,C^*$ be a cycle and a cocycle respectively. 
	  $B,B^*$ be a basis and a cobasis respectively.
	  
	  By *Wilson 32.4* every cocycle intersects with every basis at least once. By *Wilson 32.5*, the same is true for cobases and cycles. Then, by Inclusion-Exclusion and *Wilson 32.2*. 
	  
	  $$
	  \begin{equation} \begin{split}
	  |C\cup C^*|+ |C\cap C^*|&=|C|+|C^*| \\
	  |E|+|C\cap C^*| &= |B| +|B^*|+2 \\
	  |E|+|C\cap C^*|&= |E|+2 \\ 
	  |C\cap C^*| &= 2
	  \end{split}\end{equation}
	  $$

* (*Wilson e32.9*) $M$ is Eulerian if and only if $M^\ast$ is bipartite. 
	* *Remark*:  This generalizes *Wilson e15.9*.
# Links 
* [[Matroid Definitions and Constructs]]
* [[Matroid Types]]