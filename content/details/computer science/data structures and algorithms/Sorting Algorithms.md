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
* Generally performs better than Bubble and Selection Sort.
* *Worst Case*: $O(n^2)$
* *Best Case*: $O(n)$
* *Average Case*: $O(n^2)$
* *Space Complexity*: $O(1)$ auxiliary

## Selection Sort
* Divide the input into two parts -- a sorted sublist to be built up from one side (the left) of the list and an unsorted sublist consisting of the rest of the list. 
* Proceed by finding the smallest (or largest) element in the unsorted sublist and exchanging it with the leftmost unsorted element. In effect, the boundary between sorted and unsorted sublists moves left to right.
* *Worst Case*: $O(n^2)$
* *Best Case*: $O(n)$
* *Average Case*: $O(n^2)$
* *Space Complexity*: $O(1)$ auxiliary

## Merge Sort
* A divide and conquer algorithm that works as follows.
	* Recursively divide the unsorted list into $n$ sublists.
	* Sort each sublist.
	* Repeatedly merge sublists to produce new sorted sublists until only one sublist is left. This is the sorted list

![[Merge Sort.png]]
<figcaption> Merge Sort. Attribution:  VineetKumar at English Wikipedia - Transferred from en.wikipedia to Commons by Eric Bauman using CommonsHelper., Public Domain, https://commons.wikimedia.org/w/index.php?curid=8004317 </figcaption>

* *Worst Case*: $O(n\log n)$
* *Best Case*: $\Omega(n \log n)$ typical, $\Omega(n)$ 
* *Average Case*: $\Theta(n\log n)$
* *Space Complexity*: $O(n)$ auxiliary memory (using an array)

## Quick Sort
* A divide and conquer algorithm that proceeds as follows: 
	* Select a pivot element from the array. Partition the other elements into two sub-arrays. On the left of the pivot are those less than the pivot. On the right of the pivot are those greater than the pivot.
	* Sort the subarrays (either using another round of quick sort or simple sorting). 

* *Worst Case*: $O(n^2)$
* *Best Case*: $O(n \log n)$ 
* *Average Case*: $O(n\log n)$
* *Space Complexity*: $O(n)$ auxiliary memory (using an array)

![[Quick Sort.png]]
<figcaption> Quick Sort. Image taken from https://www.techiedelight.com/es/quicksort/ </figcaption>

## Heap Sort

## Radix Sort 
# Links
* [[Algorithms]]

* [[Introduction to Algorithms by Cormen, Leiserson, Rivest, and Stein|Cormen, Leiserson, Rivest, and Stein]]