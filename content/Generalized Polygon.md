* A **generalized quadrangle** is a [[Incidence Structure|partial linear space]] where
	* Given any line $L$ and point $p$ not on $L$. There is a unique point $p'$ on $L$ such that $p$ and $p'$ are collinear.
	* There are noncollinear points and nonconcurrent lines.
	* (*Godsil 5.4.1*) Let $\mathcal I$ be a partial linear space that contains noncollinear points and nonconcurrent lines. Then $\mathcal I$ is a generalized quadrangle if and only if its incidence graph $X(\mathcal I)$ has diameter $4$ and girth $8$.  
 
* (*Godsil 5.5.1*) Let $W(q)$ be the incidence structure where the points and lines are the totally isotropic points and totally isotropic lines of $\text{PG}(3,q)$.  Then $W(q)$ is a generalized quadrangle

* A **generalized [[Geometry|polygon]]** is a finite [[Bipartite Graph|bipartite graph]] with diameter $d$ and girth $2d$. We also refer to this  as a **generalized $d$-gon**. 
* A vertex $v$ in a generalized polygon is **thick** if $\deg(v)\ge 3$. Otherwise, they are **thin**.
  
  A generalized polygon is **thick** if all its vertices are thick. 

* Let $X$ be a generalized $d$-gon.
	* (*Godsil 5.6.1*) If $d(v,w)=m<d$, then there is a unique path of length $m$ from $v$ to $w$.
	* (*Godsil 5.6.2*) $d(v,w)=d\implies \deg(v)=\deg(w)$.
	* (*Godsil 5.6.3*) Every vertex in $X$ has degree at least two. 
	* (*Godsil 5.6.4*)  Any two vertices lie in a [[Trails, Walks, Paths and Cycles|cycle]] of length $2d$.
	* (*Godsil 5.6.5*) Let $C$ be a cycle of length $2d$, any two vertices at the same distance in $C$ from a thick vertex in $C$ have the same degree.
	* (*Godsil 5.6.6*) The minimum distance $k$ between any pair of thick vertices is a divisor of $d$. 
	  
	  If $d/k$ is odd, then all thick vertices have the same degree.
	  
	  If $d/k$ is even, then  the thick vertices have at most two degrees.
	  
	  Any vertices at distance $k$ from a thick vertex is itself thick
	* (*Godsil 5.6.7*)  If $X$ is not thick, it is either a cycle, a $k$-fold [[Operations on Graphs|subdivision]] of a multiple edge, or the $k$-fold subdivision of a thick generalized polygon.

* (*Godsil 5.6.8*) **Feit-Higman Theorem** If a generalized $d$-gon is thick, then $d\in\set{3,4,6,8}$. 

* (*Godsil 5.6.9*) If a generalized polygon is [[Regular Graph|regular]] it is [[Distance Transitive Graph|distance regular]]. 

* If the degrees of the vertices of a thick generalized polygon are $s+1,t+1$, we say that it has order $(s,t)$. 
* (*Godsil 5.6.10*) Let $X$ be a thick generalized $d$-gon of order $(s,t)$.  WLOG suppose $s\le t$
	* If $d=4$, then $s\le t^2$ 
	* If $d=6$, then $st=k^2$ for some $k\in\mathbb{N}$. and $s\le t^3$
	* If $d=8$, then $2st=k^2$ for some $k\in\mathbb N$ and $s\le t^2$

# Links
* [[Algebraic Graph Theory by Godsil and Royle]]