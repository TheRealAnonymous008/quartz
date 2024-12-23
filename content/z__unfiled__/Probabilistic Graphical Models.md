
* A **probabilistic graphical model**  is a  [[Fundamental Constructs of Graph Theory|graph]] that describes a [[Random Variables and Probability Distributions|probability distribution]]. 
	* In a PGM, nodes correspond to variables of the joint probability.
	* An edge between two nodes means the corresponding variables are not conditionally independent. 
	* In a [[Directed Graph|directed graphical model]], the directed edges indicate conditioning. An arc $u\to v$ indicates the factor $P(v \mid u)$. 

* A variant of this is a **factor graph** which is a [[Families of Graphs|bipartite graph]] where nodes are either variables or **factors** and edges connect between a variable and a factor.
	* An edge indicates that the variable is a part of the corresponding factor.
	* If the set of factors is $f_1,\dots, f_n$, then the joint probability distribution can be written as 
	  $$
	  p = \prod_{a\in F} f_a(x_a) 
	  $$
	  Where $x_a$ denotes the vector of neighboring variable nodes to factor node $a$. 

* PGMs allow us to perform inferences much more efficiently since we can focus on only computing factors. 