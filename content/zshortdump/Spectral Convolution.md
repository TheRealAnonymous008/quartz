* The **spectral convolution** of a graph is defined as multiplication of a node-wise signal $x\in\mathbb{R}^{|V|}$ with a [[Signal Processing|convolutional filter]] $g_\theta = \text{Diag}(\theta)$ where $\theta\in\mathbb{R}^{|V|}$ is the parameter of the filter in the [[Fourier Transform|Fourier]] domain. Thus
  
  $$
  g_\theta\star  x = U g_\theta U^T x
  $$
  Where $U$ represents the matrix of [[Matrix Diagonalization|eigenvectors]] of the normalized [[Graph Laplacian|Laplacian]] such that
  $$
  L = U\Lambda U^T
  $$
* $g_\theta$ can be understood as a function of the eigenvalues of the Laplacian.

* One approximation to $g_\theta$ is to use [[Chebyshev Polynomial|Chebyshev Polynomials]] up to $k$-th order.
  $$
  g_{\theta'}(\Lambda) = \sum_{i=0}^k \theta_k' T_k(\overline\Lambda) 
  $$
  Where
  $$
  \overline\Lambda = \frac{2}{\lambda_\text{max}} \Lambda - I
  $$
  And we define the convolution as
  $$
  g_{\theta'} \star x = \sum_{i=0}^k \theta_k' (T_k(\overline L)) x 
  $$
  Where
  $$
  \overline{L} = \frac{2}{\lambda_\text{max}} L- I
  $$
