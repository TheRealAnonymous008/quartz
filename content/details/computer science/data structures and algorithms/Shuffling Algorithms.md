### Permute By Sorting
![[Permute by Sorting.png]]
<figcaption> Permute by Sorting. Image taken from CLRS</figcaption>


* (*CLRS Lemma 5.4*) Assuming all priorities $P$ are distinct, then the input is randomly permuted. 

### Fisher-Yates 
![[Fisher Yates.png]]
<figcaption> Fisher Yates Algorithm. Image taken from CLRS</figcaption>

* (*CLRS Lemma 5.5*). This algorithm produces a uniform random permutation.
  
  This holds because of the following following loop invariant:
  
  Just prior to the $i$-th iteration of the loop, for each possible $(i-1)$-[[Permutations and Orbits|permutation]] of the $n$ elements, $\sigma$ the subarray $A[1,\dots,i-1]$ contains $\sigma$ with probability 
  
  $$
  P(\sigma) = \frac{(n-i+1)!}{n!}
  $$

# Links 
* [[Introduction to Algorithms by Cormen, Leiserson, Rivest, and Stein|CLRS]]