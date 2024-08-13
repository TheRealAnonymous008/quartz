* Geometric Deep Learning aims to provide *a common mathematical framework for neural network architectures.*
* In many cases, especially for [[Pathologies of Deep Learning|high-dimensional]] settings, we have **[[Group Theory|symmetry]] priors**  which imposes an inductive bias on the structure of the function being learnt.
	* Such priors are based on the signals on some domain $\Omega$. The domain is a vector space [^dom]
	* The space of $C$-valued signals on $\Omega$, where $\Omega$ is a set that may have additional structure and $C$ is a [[Vector Space]] of channels
	  $$
	  X(\Omega, C) = \{x : \Omega \to C \}
	  $$
	  is a function space that has a vector space structure where addition and scalar multiplication of signals is defined for all $u\in \Omega$ as 
	  $$
	  (\alpha x  + \beta y) = \alpha x(u) + \beta y(u)
	  $$
	  With $\alpha,\beta \in \mathbb{R}$. 
	  Given an inner product $\braket{v,w}_C$ and a [[Measure Theory|measure]] $\mu$ on $\Omega$, where an integral can be defined, we define the inner product on $X(\Omega,C0$ as 
	  $$
	  \braket{x,y} = \int_\Omega \braket{x(u), y(u)}_C \ \ d\mu (u)
	  $$ 

[^dom]: Think of this space as analogous to word embeddings.

# Geometric Priors
* [[Convolutional Neural Network|CNNs]] maintain equivariance (i.e., translational symmetry).
* [[Graph Neural Networks|GNNs]] and [[The Transformer Model|Transformers]] make use of permutation invariants
* [[Recurrent Neural Network|RNNs]] make use of time warping invariants.
* Another prior is **scale separation** where we produce a hierarchy of spaces by a coarse-graining operator $P$.  A function is **locally stable** if it can be approximated as the composition of coarse-graining operators.
# Links
* [Geometric Deep Learning](https://geometricdeeplearning.com/blogs/)
* [Geometric Deep Learning Grids, Groups, Graphs, Geodesics, and Gauges by Bronstein et al](https://arxiv.org/pdf/2104.13478)
* [[Geometry]] - GDL aims to mimic the unification of various geometries by studying the invariants of these geometries.
