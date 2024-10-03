* Let $N\unlhd G$ be a [[Normal Group|normal subgroup]] of $G$. 
  
  The **factor group** (also called **quotient group** of $G$ modulo $N$, denoted $G/N$ is the group formed from the [[Cosets, Group Indices|coset]] of $N$ (i.e. the set $\{aN \mid a\in G\}$) where 
  $$
  (aN)(bN)=(ab)N
  $$
  It has an [[Group Isomorphism|isomorphism]] $\mu:G/N\to \phi(G)$ defined as 
  $$
  \mu(aN)=\phi(a)
  $$
  Both coset multiplication and the isomorphism are independent of $a,b$.
  
  See (*Fraleigh 14.4*) for a proof that $N$ being a normal subgroup is necessary and sufficient for coset multiplication to be well defined. 
	* In effect, this simplifies the group structure by *representing all [[Cosets, Group Indices|Cosets]] with a representative element*.
	* (*Fraleigh 14.5*) The set of cosets forms a group
		* In the factor group $G/N$, the coset $N$ serves as $0$.
	* (*Fraleigh 14.1*) One natural choice for $N$ is the [[Group Homomorphism|Kernel]] of the homomorphism $\phi:G\to G'$

* For any group $G/\{e\} \cong G$ and $G/G \cong \{e\}$

* (*Fraleigh 14.9*)  Let $N\unlhd G$. Then $\gamma : G\to G/N$ where 
  $$
  \gamma(x)=xN
  $$
  is a homomorphism with kernel $N$.

* (*Fraleigh 15.8*) Let $G=H\times K$. Then, $\overline{H}=\{(h,e)\mid h\in H\}$ is a normal subgroup of $G$. Also, $G/\overline{H}\cong K$ in a natural way. Similarly, $G/\overline{K}\cong H$ in a natural way.  [^15.8]
	* For $G/\overline H \cong K$ take the homomorphism $\phi(h,k) = k$.
	* For $G/\overline K \cong H$ take the homomorphism $\phi(h,k) =h$


[^15.8]: See [[Direct Product of Groups]]

* (*Fraleigh 15.9*) The factor group of a cyclic group is [[Cyclic Group|cyclic]]. 
# Links
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh]]