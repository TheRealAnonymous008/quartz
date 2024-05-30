* **Direct Addressing** is a simple variant for implementing dictionaries. Here, *each position in the array is associated with a key*. 
	* This is relatively easy to implement.
	* If the set of keys is large, this is impractical to implement considering memory constraints. 
	* If the set of keys actually used is really small, this will result in significantly wasted space. 

* A **hash table** implements a look-up table or dictionary such that searching is $O(1)$ instead of the typical $O(n)$.  
	* *Hash tables are effective when the number of keys stored is small relative to the total number of possible keys*.
	* Hash tables require the use of a **hash function** $h(k)$ which maps a key $k$ to a slot in the hash table. We assume that the hash table size $|T|$ is significantly smaller than the number of possible values. 
	* Hash functions must be robust against *collisions* where two keys map to the same hashed values. 
		* The **load factor** $\alpha$ of a hash table $T$ with $m$ slots storing $n$ elements is defined as 
		  $$
		  \alpha = \frac{n}{m}
		  $$
		  It is the average number of keys that map to the same slot. 

# Collision Resolution
* **Chaining** means placing all elements that hash to the same slot into the same linked list. 
	* Insertion takes $O(1)$ time
	* Deletion (assuming doubly linked lists) take $O(1)$ time
	* The search time depends on the load factor. 
		* In the worst case, it is $\Theta(n)$ if all keys map to the same slot (i.e., same search time as a linked list)
		* (*CLRS 11.1, CLRS 11.2*) In a hash table where collisions are resolved by chaining, a search, whether successful or not, takes average case time $\Theta(1+\alpha)$ under the assumption of simple uniform hashing. 
		  
		  The $1$ comes from the fact that we still need to compute the hash.

* In an **open addressing** scheme, all elements occupy the hash table itself. In such a scheme, $\alpha \le 1$. 
	* Open addressing necessitates **probing** to find a slot where we put the key. This requires us to extend the hashing function to include the probing number as input. We call this new hash function the **auxiliary hash function**
	  
	  For every $k$, the probe sequence $h(k,0), h(k,1),\dots, h(k,m-1)$ is a [[Permutations and Orbits|permutation]] of the identity sequence. This way *every slot is eventually considered as a candidate*. 
	* Inserting with a probing scheme means considering each slot in the probe sequence for the key until an empty slot is found.
	* *Probing methods tend to not give uniform hashing out of the box*
	* (*CLRS 11.6, CLRS 11.8*) Given an open address hash table with uniform hashing, the expected number of probes $N$ is given by
	  
		$$
		N \le 
		\begin{cases}
		\frac{1}{1-\alpha} & \text{if search is unsuccsesful} \\
		\frac{1}{a} \ln \frac{1}{1-\alpha} & \text{if search is successful}
		\end{cases} 
		$$
		Where we assume that each key is equally likely to be searched for.
		* (*CLRS 117*) Inserting an element into an open address hash table requires at most $\frac{1}{1-\alpha}$ probes on average, assuming uniform hashing
## Probing
* **Linear Probing** means that our auxiliary hash function is given by 
  $$
  h(k,i) = (h'(k) + i) \text{ mod } m
  $$
  That is, we simply probe all slots in order. 
	* We use $\Theta(m)$ probe sequences at most. 
	* This is simple to implement.
	* However, it suffers from **primary clustering** where we have long runs of unoccupied slots and long runs tend to become longer.

* **Quadratic Probing** means using an auxiliary hash function given by
  $$
  h(k,i) = (h'(k) + c_1i + c_2 i^2 ) \text{ mod }m  
  $$
  Where $c_1, c_2 > 0$ are constant. 
	* We use $\Theta(m)$ probe sequences at most. 
	* A slight improvement to linear probing that also reduces primary clustering.
	* However, it suffers from **secondary clustering** wherein long runs are formed indirectly as a result of two keys having the same initial probe positions.

* **Double Hashing** means using an auxiliary hash function defined by two other  hash functions $h_1, h_2$ 
  
  $$
  h(k,i) = (h_1(k) + ih_2(k)) \ \text{mod m}
  $$
	* $h_2(k)$ must be relatively prime to the hash table size to search the entire hash table. 
	* We use $\Theta(m^2)$ probe sequences with a prime or power of $2$ m. 

# Hash Functions
* **Simple Uniform Hashing** assumes that all keys are equally likely to hash to any of the $m$ slots independent of any other element.
	* *Ideally a hash function should match simple uniform hashing*
* In practice, we can often employ heuristic techniques to create a hash function that performs well.
* *Hash function should be entropic*. There should be no apparent patterns

* The **division method** performs hashing as follows
	$$
	h(k) = k \ \ \ \ \text{mod}  \ m
	$$
	* Certain values of $m$ should be avoided (I.e., numbers that are powers of numbers )
	* Often a good choice is a [[Number Theory|prime]] not close to an exact power of $2$.
* The **multiplication method** operates with constant $0<A<1$. and performs the following
  
	$$
	h(k) = \lfloor m \ \{k \ A\} \rfloor
	$$
	Where $\{x\}$ denotes the fractional part of $x$.
	* The value of $m$ is not critical (often we can choose it to be a power of $2$.
	* The value of $A$ is critical. Onne suggestion from Knuth is 
	  
	$$
	A\approx \frac{\sqrt 5 -1}{2}
	$$

* **Universal Hashing** means *choosing a hash function randomly independent of the keys actually stored*. 
	* At the beginning of execution, we choose a hash function from a set $\mathcal{H}$ of hash functions mapping universe $U\to \{0,1,\dots,m-1\}$.  
	  
	  $\mathcal{H}$ is **universal** if each pair of distinct keys $k,l\in U$, the number of hash functions $h\in \mathcal{H}$ for which $h(k)=h(l)$ is at most $\frac{|\mathcal{H}|}{m}$. 
		* (*CLRS 11.3*) Suppose a hash function $h$ is chosen randomly from a universal collection of hash functions and has been used to hash $n$ keys into a table $T$ of size $m$, using chaining to resolve collisions. If key $k$ is not in the table, then the expected length $\mathbb{E}[n_{h(k)}]$ of the list that key $k$ hashes to has the following bounds
		  
		$$
		\mathbb{E}[n_{h(k)}]  \le 
		\begin{cases}
		\alpha & \text{if } k \in T  \\ 
		1 + \alpha & \text{otherwise} 
		\end{cases}
		$$

		* (*CLRS 11.4*) Using universal hashing and collision resolution by chaining in an initially empty table with $m$ slots, it takes expected time $\Theta(n)$ to handle any sequence of $n$ insert, search, and delete operations containing $O(m)$ insert operations


	* Universal hashing allows us to avoid the downside of other fixed hashing functions -- wherein an adversary can choose keys that map to the same slot. 

	* A universal class of hash functions can be designed as follows.
	  
	  Let $p$ be a prime large enough so that $k\in [0,p-1]$. Denote $\mathbb{Z}_p=\{0,1,\dots,p-1\}$ and $\mathbb{Z}_p^\ast=\mathbb{Z}_p-\{0\}$.
	  
	  The hash function $h_{ab}$ for $a\in \mathbb{Z}_p^\ast$ and $b\in\mathbb{Z}_p$ using the following linear transformation reduced modulo $p$ and $m$. 
	  $$
	  h_{ab} = ((ak+b) \ \text{mod } p) \ \text{mod } m
	  $$
	  The family of all such functions is denoted $\mathcal{H}_{pm}$. 
	  
	  (*CLRS 11.5*) says that $\mathcal{H}_{pm}$ is universal


* We say that a hashing technique is **perfect** if $O(1)$ memory accesses are required to perform a search in the worst case. 
	* This can be achieved using two layers of hash table, each using universal hashing (we denote the universal class as $\mathcal{H}$) . The second table should use a hash function that guarantees no collisions. 
		* Ideally, the second table should also have a size that is the square of the first table 
		* In practice, if the first table is already too big, we can settle for two level hashing where we hash entries in each slot.
	* (*CLRS 11.9*) If we store $n$ keys in a hash table of size $m=n^2$ using a hash function $h\sim\mathcal{H}$, then the probability of collisions is less than $\frac12$.  [^clrs_119]
	* (*CLRS 11.10*) Suppose we store $n$ keys in a hash table of size $m=n$ using hash function $h\sim \mathcal{H}$. We have that
	  
	  $$
	  \mathbb{E}\bigg[\sum_{j=0}^{m-1} n_j^2\bigg] < 2n
	  $$
	  Where $n_j$ is the number of keys hashing to slot $j$.
		* (*CLRS 11.11*) If we store $n$ keys in a hash table of size $m=n$ using $h\sim\mathcal{H}$ and set the size of each secondary hash table to $m_j=n_j^2$, then the expected amount of storage required for all secondary hash tables in a perfect hashing scheme is less than $2n$.  
		* (*CLRS 11.11*) Following (*CLRS 11.11*), the probability that the total storage used for secondary hash tables exceeds $4n$ is less than $\frac{1}{2}$. *We can simply test a few randomly chosen hash functions to find one that uses a reasonable amount of storage*.


[^clrs_119]: This follows from [[Random Variables and Probability Distributions|Markov's Inequality]]. 

# Links
* [[Introduction to Algorithms by Cormen, Leiserson, Rivest, and Stein|CLRS]] - Ch. 11