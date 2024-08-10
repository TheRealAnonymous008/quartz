* The study of linear transformations in space. It deals with vector spaces and matrices. 

* **Batch Matrix Multiplication** is an operation $\text{BMM}$ that extends matrix multiplication to allow it to be performed per batch.
  
  More formally, if we have inputs
  $$
  \begin{equation} \begin{split}
  A &= [A_1, \dots, A_n] \in \mathbb{R}^{n\times a \times b} \\
  B &= [B_1, \dots, B_n] \in \mathbb{R}^{n\times b \times c} \\
  \end{split}\end{equation}
  $$
  Then 
  $$
  \text{BMM}(A,B)=[A_1 B_1, \dots, A_n B_n] \in \mathbb{R}^{n\times a \times c}
  $$


# Topics
* [[Matrix Inversion]]
* [[Vector Field]]
# Links
* [[Machine Learning - A Probabilistic Perspective by Murphy|Murphy Ch. 4.3.4.1]]

* [[Linear Algebra by Friedberg Insel and Spence]]