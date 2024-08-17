* The best we can do for a comparison-based sorting algorithm is $\Theta(n\log n)$. 
	* The intuition is as follows: We can frame sorting as a search operation applied on a list of [[Permutations and Orbits|permutations]] on a decision [[Binary Search Tree|Tree]] where internal nodes correspond to comparison and swap operations. There are $n!$ permutations for a list of $n$ elements and the best we can do is binary search which will take $\log(n!)$ time. 
	  
	  Stirling's approximation then gives that $\log(n!)\approx n\log n + n + O(\log n)$.   

## Bubble Sort
* Compare the current element with the one after it. Swap their values if needed. Sorting stops when no more swaps can be performed.
* The larger elements bubble to the top of the list.
* *Worst case*: $O(n^2)$
* *Best Case*: $O(n)$
* *Average Case*: $O(n^2)$
* *Space Complexity*: $O(1)$ auxiliary.

## Insertion Sort
* Remove one element from the input data, find where it goes in the sorted array and insert it there.
* *Worst Case*: $O(n^2)$
* *Best Case*: $O(n)$
* *Average Case*: $O(n^2)$
* *Space Complexity*: $O(1)$ auxiliary
# Links
* [[Algorithms]]

* [[Introduction to Algorithms by Cormen, Leiserson, Rivest, and Stein|Cormen, Leiserson, Rivest, and Stein]]