* The best we can do for a comparison-based sorting algorithm is $\Theta(n\log n)$. 
	* The intuition is as follows: We can frame sorting as a search operation applied on a list of [[Permutations and Orbits|permutations]] on a decision [[Binary Search Tree|Tree]] where internal nodes correspond to comparison and swap operations. There are $n!$ permutations for a list of $n$ elements and the best we can do is binary search which will take $\log(n!)$ time. 
	  
	  Stirling's approximation then gives that $\log(n!)\approx n\log n + n + O(\log n)$.   



# Links
* [[Algorithms]]

* [[Introduction to Algorithms by Cormen, Leiserson, Rivest, and Stein|Cormen, Leiserson, Rivest, and Stein]]