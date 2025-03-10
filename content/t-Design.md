* A **$t$-Design** is an [[Incidence Structure|incidence structure]]
  
  More specifically, a $t-(v,k,\lambda_t)$ design is a set of $v$ points, with a collection $\mathcal B$ of $k$-subsets of points called **blocks** such that every $t$-set of points lies in precisely $\lambda_t$ blocks

* The [[Projective Plane|projective planes]] $\text{PG}(2,q)$ have the property that every two points lie in a unique block.
  
  They are therefore $2=(q^2+q+1,q+1,1)$ designs

* Let $\mathcal D$ be a $t-(v,k,\lambda_t)$ design and $S$ a set of points where $|S|=s<t$. 
  
  We have
  $$
  \lambda_s { k-s\choose t-s} = \lambda_t {v - s \choose t- s}
  $$
  So that $\mathcal D$ is also an $s-(v,k,\lambda_s)$ design. 
* A $t$-design exists if  $\lambda_s$ is an integer for all $s<t$. 

* $b=\lambda_0$ denotes the total blocks of the design.
* $r=\lambda _1$ is the **replication number** which denotes the number of blocks containing each point.
* $$
  bk = vr
  $$

* (*Godsil 5.10.1*) In a $2$-design with $k\le v$, we have $b\ge v$.

* A $2$-design with $b=v$ is called **symmetric**.
* (*Godsil 5.10.2*) The dual $\mathcal D^\ast$ of a symmetric design $\mathcal D$ is a symmetric design with the same parameters

* (*Godsil 5.10.3*) A [[Bipartite Graph|bipartite graph]] is the incidence graph of a symmetric $2$-design if and only if it is [[Distance Transitive Graph|distance regular]] with diameter $3$

* The **incidence matrix** of a design is the matrix $N$ where rows are indexed by points, columns by blocks.
  
  $N_{ij}=1$ if the $i$-th block in the $j$-th block. 
* $N$ satisfies
  $$
  NN^T = (r-\lambda_2) I + \lambda_2 J
  $$
  Where $J$ is the all one's matrix. 


# Steiner system
* A **Steiner System** is one where $\lambda_t=1$. 
* A **Steiner Triple system** is a $2$-design with $\lambda_2=1$, and $k=3$.

* (*Godsil 5.10.4*) The block intersection graph of a Steiner triple system with $v>7$ is distance regular with diameter $2$.
# Links
* [[Algebraic Graph Theory by Godsil and Royle]]