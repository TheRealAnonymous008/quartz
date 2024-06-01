 * [[Automata Theory]]
	 * [[Finite Automata and Regular Languages]]
	 * [[Pushdown Automata and Context Free Languages]]

* The **RAM model** is defined as consisting of the following:
	* Infinitely long memory. Each register in memory stores one natural number of any size. 
	* An instruction set, typically consisting of:
		* Basic comparator and arithmetic operations assumed to take $O(1)$ time.
		* Memory read and write which takes $O(1)$ time.
		* Loops which take $O(n)$ time depending on the size of the loop.

* The **external memory model (a.k.a. cache aware model)** is similar to the RAM model but with a [[Cache Memory]] in addition to main memory. 
	* Here, we capture the fact that reads to the cache are faster than memory, and reading contiguous blocks is faster than reading randomly.  *In general, we are able to capture the memory hierarchy when relevant*. 
	* The runtime of an algorithm is defined using the number of reads and writes to memory required. 
	* *It is applicable to datasets too big to fit in memory.*

* The **cache oblivious model** is designed to take advantage of a processor cache without having the length of cache lines as an explicit parameter. 
  
  In other words, we do not take advantage of any knowledge of how many cache lines and how big they are. 
	* Memory is broken into blocks of size $B$
	* A load or store between main memory and storage can be performed between cache and memory. 
	* The cache is fully associative.
	* The replacement policy is assumed optimal (in practice, Least Recently Used). It has an oracle which will look into future requests and evict the line whose first access is furthest in the future. 
	* The complexity of an algorithm is measured in the number of cache misses. The runtime is the number of transfers between cache and main memory. 
	* *What is efficient in cache oblivious models is likely efficient on real machines.*

* The **Parallel RAM / PRAM** model is the [[Multiprogramming|parallel]] computing version of the RAM model -- similar to RAM, PRAM is used for analyzing parallel algorithms without regard for synchronization or process communication.
  
  In PRAM, we have possibly multiple parallel processors.
  
  Algorithmic complexity is estimated as either regular time taken or time taken multiplied by processor number.
	* There are variants based on how to resolve read and write conflicts. 
		* **EREW  (Exclusive Read Exclusive Write** - every memory cell can be read or written to by only one processor at a time
		* **CREW (Concurrent Read Exclusive Write** - multiple processors can read a memory cell, but only one can write at a time.
		* **ERCW (Exclusive Read Concurrent Write** - multiple processors can write but only one can read. Typically does not add power. 
		* **CRCW (Concurrent Read, Concurrent Write** - multiple processors can read and write. 
	* Concurrent writes can be further defined as:
		* **Common** - all processors must write the same value, otherwise it is illegal.
		* **Arbitrary** - only one arbitrary attempt is successful.
		* **Priority** - the processor with highest priority is the one that writes.
	* We assume the following:
		* There is no limit on the number of processors.
		* All cells can be accessed from any processor.
		* No limit on shared memory in the system.
		* No resource contention
		* SIMD instructions


* The **Bulk Synchronous Parallel (BSP) model**  is an extension of PRAM wherein concurrency and synchronization are considered.
	* The model consists of a set of processors that may be multithreaded. Each processor has fast local memory and can communicate or synchronize with each other.
	* Computation proceeds with supersteps that proceed as follows
		* Concurrent computation - all processors perform local computations (either asynchronously or overlapping with each other)
		* Communication - all processors exchange data. This comes in the form of sending and receiving messages en masse (hence bulk) [^BSP_1] 
			* The maximum number of messages for a superstep is denoted $h$. The ability of the network to facilitate communication is captured by parameter $g$ such that it takes time $hg$ for a processor to deliver $h$ messages of size $1$.
			* The cost of delivering a message of size $m$ is $mg$
			* $g$ depends on 
				* Network protocols
				* Buffer management
				* Routing strategy
				* Runtime system. 

		* Synchronization - wait until all processes have reached the same point (called a barrier) .
			* A barrier means deadlock is not a  concern. 
			* The cost of barrier synchronization, denoted $l$ depends on
				* The cost imposed by variance in completion time for concurrent processes.
				* The cost of reaching a globally consistent state for all processors, dependent on the communication network. 

	* The cost of a superstep is defined, for $p$ processors with local computation cost $i$ and local communication cost $h_i$ is 
	  
	  $$
	  \max_{i=1}^p (w_i) + \max_{i=1}^p (h_ig) + l
	  $$
	  The cost of the entire algorithm is the sum of all supersteps.

[^BSP]: By having it be done en masse, we can generate an upper bound for the time communication takes.