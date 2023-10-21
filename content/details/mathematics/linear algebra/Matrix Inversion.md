* *Murphy  Thm. 4.3.2* Let 
  $$
  M=\begin{pmatrix}E & F \\ G & H\end{pmatrix}
  $$
  Where $E$ and $H$ are invertible. We have
  $$
  \begin{split} M^{-1}&=\begin{pmatrix}
  (M/H)^{-1} &
  -(M/H)^{-1}FH^{-1} \\ 
  -H^{-1}G(M/H)^{-1} & 
  H^{-1}+H^{-1}G(M/H)^{-1}FH^{-1})
  \end{pmatrix}
  \\ 
  &= \begin{pmatrix}
  E^{-1}+ E^{-1}F(M/E)^{-1}GE^{-1} &
  -E^{-1}F(M/E)^{-1} \\ 
  -(M/E)^{-1}GE^{-1} & 
  (M/E)^{-1}
  \end{pmatrix}
  \end{split}
  $$
  
  Obtain the second formula, by interchanging the two diagonal entries of the first and then interchanging all $H$ with $E$ and all $F$ with $G$.
  
  We also have the  **Schur Complements**
  $$
  \begin{split}M/H&= E-FH^{-1}G \\ 
  M/E&= H-GE^{-1}F
  \end{split}
  $$
  The Schur Complements arise when performing Gaussian Elimination on the block matrix

* *Murphy Cor. 4.3.1.* Let 
  $$
  M=\begin{pmatrix}E & F \\ G & H\end{pmatrix}
  $$
  Where $E$ and $H$ are invertible. We have  
  $$
  \begin{split}(E-FH^{-1}G)^{-1}&=E^{-1}+E^{-1}F(H-GE^{-1}F)^{-1}GE^{-1} \\ 
  
  (E-FH^{-1}G)^{-1}FH^{-1}&=E^{-1}F(H-GE^{-1}F)^{-1} \\ 
  
  |E-FH^{-1}G|&= |H-GE^{-1}F||H^{-1}||E|
  
  \end{split}
  $$
  The first two are called the **Matrix Inversion Lemma** or the **Sherman-Morrison-Woodbury Formula**.  The last is called the **Matrix Determinant Lemma**.
  
  The **Sherman-Morrison formula** is an important special case given as 
  
  $$
  (A+uv^T)^{-1}=A^{-1}-\frac{A^{-1}uv^TA^{-1}}{1+v^TA^{-1}u}
  $$
  
  Where we assume $1+v^TA^{-1}u\ne 0$. 


* The **Bunch-Nielsen Sorensen formula** is as follows. 
  
  Let $\lambda_i$ denote the eigenvalues of $A_i$ and 
  
  $\overline{\lambda_i}$ denote the eigenvalues of the updated matrix $\overline{A}=A+vv^T$.
  
  In the special case when $A$ is diagonal, the eigenvalues $\overline{q}$ of $\overline{A}$ is given as 
  
  $$
  (\overline{q_i})_k = \frac{N_i \ v_k}{\lambda_k-\overline{\lambda_i}}
  $$
  
  Where $N_i$ is a number that makes $\overline{q_i}$ normalized.
# Links
* [[Machine Learning - A Probabilistic Perspective by Murphy|Murphy 4.3.2.1]]