* Let $V$ be a [[Vector Space|vector space]] and $W_1\le V$. A function $T:V\to V$ is called a **projection** on $W_1$ if
	* There exists $W_2\le V$ such that $V = W_1 \oplus W_2$. [^oplus]
	* For $x=x_1 + x_2$ where $x_1\in W_1$ and $x_2 \in W_2$ we have $T(x)=x_1$
* (*Friedberg e2.1.22*) $T$ is [[Linear Transformation|linear]]
* (*Frieidberg e2.1.23*) If $W_1=R(T)$, then $W_2=N(T)$ so that
  $$
  V = N(T) \oplus R(T)
  $$
* (*Friedberg e2.3.14*) $T$ is a projection if and only if $T=T^2$ (that is, applying the projection twice has the same effect as applying it once)

 * A linear operator $T$ on $V$ is called **nilpotent** if $T^p=T_0$ for some positive integer $p$.

# Links
* [[Linear Algebra by Friedberg Insel and Spence|Friedberg, Insel and Spence]]