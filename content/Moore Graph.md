* A **Moore [[Fundamental Constructs of Graph Theory|graph]]** is a graph with diameter $d$ and girth $2d+1$. 

* There are  four known Moore graphs
	* $K_n$ where $n>2$. 
	* $C_{2n+1}$ : The odd cycles .(see [[Trails, Walks, Paths and Cycles|cycles]])
	* The [[Generalized Johnson Graph#Petersen Graph|Petersen Graph]]
	* The Huffman Singleton graph.

* (*Godsil 5.8.1*) A Moore graph is [[Regular Graph|regular]].
* (*Godsil 5.8.2*) A Moore graph is [[Distance Transitive Graph|distance regular]].
	* Moore Graphs of diameter greater than $2$ do not exist.
	* A Moore graph of diameter $2$ must be $k$-regular $k\in\set{2,3,7,57}$.

* (*Godsil 5.9.1*) An independent set $C$ in a Moore graph of diameter $2$ and degree $7$ contains at most $15$ vertices. 
  
  If $|C|=15$ then every vertex not in $C$ has exactly $3$ neighbors in $C$.


# Hoffman-Singleton Graph
* One way to construct the **Hoffman Singleton Graph** is as follows: 
  
  Take $5$ pentagons $P_h$ and $5$ pentagrams $Q_i$. Follow the adjacency rule where $j\in V(P_h)$ and $q\in V(Q_i)$.
  $$
  jh\in E(X) \iff h\cdot i + j \equiv q  \mod 5 
  $$

* Another way is using heptads.
	* Choose an $\text{Alt}(7)$ [[Permutations and Orbits|orbit]] of heptads from $\Omega = \set{1,\dots,7}$. 
	* The vertices of the Huffman Singleton graph are the heptads and the triples.
	* A heptad is joined to a triple if and only if it contains the triple.
	* A triple is joined to a triple if and only if they are disjoint.



![[Huffman Singleton Graph.png]]
<figcaption> The Huffman Singleton Graph By Uzyel - Own work, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=10378641</figcaption>


# Links
* [[Algebraic Graph Theory by Godsil and Royle]]