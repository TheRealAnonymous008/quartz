* The **confidence loss** is a loss function denoted $L_{conf}$. It measures the loss on the confidence scores.
  
  Let 
  $x_{ij}^p=\{1,0\}$ be an indicator for matching the $i$-th  anchor box to the $j$-th ground truth box
  
  $c_i^p$ be the confidence function of the $i$-th default box for class $p$
  
  $Pos$ denotes the set of positive anchor boxes (i.e., those that predicted an object class)
  
  $Neg$ denotes the set of negative anchor boxes (i.e., those that predicted the background)
  
  We have 
  
  $$
  L_{conf}(x,c)=-\sum_{i\in Pos}^N x_{ij}^p \log(c_i'^p) - \sum_{i\in Neg}\log(c_i'^0)
  $$
  Where 
  $$
  c_i'^p= \text{softmax}(c_i^p)
  $$
