* A $\updelta$-**shaped sequence** is a sequence $h_N$ of nonnegative [[Real Analysis|smooth]] functions equal to $0$ outside neighborhoods that tend to $0$ as $N\to\infty$ and each possessing an integral of $1$.

* The **Dirac Delta Function** is defined such that
  $$
  \lim_{N\to\infty} h_N = \delta
  $$
  Of course, no such function exists, but we treat it as if it were any other mathematical object. 

* For any continuous function $g$, we have
  $$
  \lim_{N\to\infty} \int_{-\infty}^\infty h_N(x) g(x) \ dx = g(0)
  $$
  And also
  $$
  \int_{-\infty}^\infty \delta (x) g(x) \ dx = g(0)
  $$
* Translation by $\xi$ along the $x$-axis preserves this property
  $$
  \int_{-\infty}^\infty \delta(x-\xi) g(x) \ dx = g(\xi)
  $$
  We refer to this as the **$\delta$- function concentrated on $\xi$** denoted $\delta(\cdot -\xi)$.

# Links
* [[Ordinary Differential Equations by Arnold|Arnold]]