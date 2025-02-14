* A [[Fundamental Constructs of Graph Theory|graph]] is **asymmetric** if its [[Graph Automorphism|automorphism group]] is the identity group. 

* (*Godsil 2.3.3*) Almost all graphs are asymmetric.
	* *Proof*: Let the proportion of asymmetric [[Graph Isomorphism|isomorphism]] classes on $V$ be $\mu$.  Note that the proportion of asymmetric graphs will be larger than $\mu$ so $\mu$ gives a lower bound.
	  
	  Each isomorphic class of a graph that is not asymmetric contains at most $\frac{n!}{2}$ graphs.
	  
	  On the other hand, by (*Godsil 2.3.2*), the average size of an isomorphism class is at most
	  $$
	  n!\left(\mu + \frac{1-\mu}{2}\right)= \frac{n!}{2}(1+\mu)
	  $$
	  And 
	  $$
	  \frac{n!}{2}(1 + \mu) (1 + o(1)) \frac{2^{n\choose2}}{n!} > 2^{n\choose 2}
	  $$
	  Observe that $\lim_{n\to \infty} \mu = 1$. 

# Links
* [[Algebraic Graph Theory by Godsil and Royle]]