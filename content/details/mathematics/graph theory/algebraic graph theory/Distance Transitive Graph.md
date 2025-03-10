* A [[Graph Connectivity|connected graph]] $X$ is **distance transitive** if given any two order pairs $(u,u')$ and $(v,v')$ such that $d(u,u')=d(v,v')$, there is an [[Graph Automorphism|automorphism]] $g$ of $X$ such that $(v,v')=g(u,u')$

* Distance transitive graphs are at least $1$-[[s-Arc Transitive Graph|arc transitive]]. 

* An alternate characterization is provided as follows
  Let $X_i(u)$ be the set of vertices at distance $i$ from $u$ and $d$ the diameter of the graph. The partition
  $$
  \set{u,X_1(u),\dots, X_d(u)}
  $$
  is the **distance partition** with respect to $u$
	* $G$ acts [[Transitive Group|transitively]] on $X_i(u)$. Thus, each cell in the distance partition acts as an [[Permutations and Orbits|orbit]] of $G$ 
	* If $X$ has diameter $d$, then $G$ acts distance transitively on $X$ if and only if it acts transitively and for any $u\in V(X)$, the stabilizer $G_u$ has exactly $d+1$ orbits. 
	* The graph induced by any cell in the partition is [[Regular Graph|regular]]. 
	* The graph induced by any pair of cells is semi-regular.

* The **parameters** of a distance transitive graph are a set of triple $a_i,b_i,c_i$ for $i=0,\dots, d$. Let $u\in X_i$, 
  $a_i$ = number of vertices $u$ is adjacent to in $X_i(u)$
  $b_i$ = number of vertices $u$ is adjacent to in $X_{i+1}(u)$
  $c_i$ = number of vertices $u$ is adjacent to in $X_{i-1}(u)$
	* The **intersection array** is a [[Matrix|matrix]] recording these parameters
	  $$
	  \begin{bmatrix}
	  - & c_1 & \dots & c_{d-1} & c_d \\
	    a_0 & a_1 & \dots & a_{d-1} & a_d \\
	    b_0 & b_1 & \dots & b_{d-1} & -
	  \end{bmatrix}
	  $$
	* $\forall i \ : \ c_i+a_i +b_i = k$ where $k$ is the degree of the graph. 
	* An abbreviated version of the intersection array is simply $\set{b_0,\dots,b_{d-1}, c_1,\dots, c_d}$ 

* $X$ is **distance regular** if the intersection array is well defined and the same for each vertex.
	* *Every distance transitive graph is distance regular*. But the converse is not necessarily true.

* (*Godsil e4.14*) An $s$-arc transitive graph with girth $2s+1$ has diameter $s$ and is distance transitive. 
	* Let $X$ be this graph, and $u,v\in V(X)$. Let $P$ be a shortest path between $u$ and $v$. If $d(u,v)>s$ then $P$ must contain an $s$-arc which can be mapped to an $s$-arc in the cycle of length $2s+1$. However, the distance between two vertices in this cycle is at most $s$ which would yield a shorter shortest path. Therefore $d(u,v)\le s$. Additionally, any two points in the cycle have distance at most $s$. Therefore, $d(u,v)\ge s$. Therefore $d(u,v)=s$. 
	    
	  Let $P$ be the shortest path between $u$ and $v$. Clearly $|P|\le s$ since the diameter is $s$ and so $P$ can be mapped to any other $|P|$-arc by automorphism because of $s$-arc transitivity. Therefore, shortest paths are preserved and so are distances. Therefore, $X$ is also distance transitive .
# Links
* [[Algebraic Graph Theory by Godsil and Royle]]