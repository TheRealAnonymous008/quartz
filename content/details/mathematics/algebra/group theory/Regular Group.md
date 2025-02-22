
* A permutation group $G$ acting on $X$ is **semiregular** if no non-identity element of $G$  fixes a point of $X$.
	* If $G$ is semiregular, then all all orbits have length equal to $G$. 
* A permutation group is **regular** if it is semiregular and [[Transitive Group|transitive]]. 
	* If $G$ is regular on $X$, then $|G|=|X|$. 
	* The group $G$ acts on itself regularly. 

* (*Godsil e3.8*) A transitive [[Abelian Group|Abelian]] permutation group is regular.
	* *Proof*: Let $G$ be a transitive Abelian permutation group. We show that $G$ is semi-regular. Let $x\in X$ be fixed by $g$. By transitivity, there exists $h\in G$ such that for any $y$, $hx=y$.  Since $G$ is Abelian
	  $$
	  gy = gh x = hgx = hx = y 
	  $$
	  Thus  $\forall y, gy = y$ which means $g=e$. Therefore, $G$ is semi-regular and in combination with transitivity, regular. 
	   
	  
# Links
* [[Algebraic Graph Theory by Godsil and Royle]]

* [[Group Action]]
* [[Symmetric Group]]