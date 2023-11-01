# What is the Cache?
* A **cache** is used by the CPU to reduce the average cost of accessing data from the RAM.
	* The cache is a smaller, faster memory located closer to the CPU which stores copies of commonly used memory addresses.
	* Cache memory is a construct in the memory hierarchy that allows us to *exploit spatial and temporal locality* to boost the performance of our program.
		* **Spatial Locality** - items that are contiguous those accessed recently are likely to be accessed soon (via Sequential Access)
		* **Temporal Locality** - items accessed recently are likely to be accessed again (i.e., induction variables or instructions in a loop)
	* To speed up access, the processor first checks for the cache memory for the requested memory location. 

* A **cache line** or **cache block** is a unit of copying in the context of cache memory. 
	* When a cache line is copied from memory into the cache, a cache entry is created. This will include the copied data and the requested memory location (called a **tag**).
	* We also include a **valid bit** which is a bit  that denotes whether or not this cache was populated. Initially, on startup this bit is set to $0$. It is set to $1$ if there is data stored in this block.

* A **cache hit** occurs when data being accessed was found in a cache block.
* A **cache miss** occurs when data accessed was not found in a cache block and so it must be accessed from main memory. 
	* What follows after a cache miss depends on the [[#Cache Policies|policy]].

# Performance Measures
* The **hit time** is the time required to access the cache, including the time needed to determine if it was a hit or a miss.

* The **hit ratio** is defined as 
  $$
  \text{hit ratio}=\frac{\text{cache hits}}{\text{accesses}}
  $$

* The **miss penalty** pertains to the additional time a processor needs to scan the memory to find the requested data that was not in the cache.

* The **miss ratio** is defined as 
  $$
  \text{miss ratio}=1-\text{hit ratio}
  $$

* The **average cache memory access time**, denoted $T_{\text{avg}}$ is defined as 
  $$
  T_{\text{avg}}=hC+(1-h)M
  $$
  Where 
  $h$ is the hit ratio
  $C$ is the cache access time
  $M$ is the miss penalty.*

# Cache Policies
## Cache Placement Policy
* Determines where a block of memory will be mapped to the cache.
### Direct-Mapped
* Organized into multiple sets, with a *single cache line per set*. The mapping is done based on the  memory address, where a single memory block can only occupy a single cache line. 
* We may frame this as viewing the cache as a $n$-long column  vector.  
* If the cache contains $2^k$ blocks then the data at memory address $i$ is mapped to the cache block with index $i\mod{2^k}$. 

#### Handling Block Queries
1. Determine the index using the address of the memory block. In particular, we look at the least significant bits.
2. Determine the actual memory address of interest using the tags. The tag consists of the bits that were not used in the index (i.e., they are the remaining most significant bits). 

#### Advantages
* Simple replacement and placement policy
* Cheap hardware needed.
* Power efficient

#### Disadvantages
* Lower hit rate as there is only one cache available in a set.
* Every time new memory is referenced to the same set, the cache line is replaced, causing a miss.

### Fully Associative 
* Cache is organized into a single set, with *multiple cache lines per set*. The mapping is such that any memory block can occupy any of the cache lines. 
* This organization can be framed as a row vector

#### Block Query
* The tag field of the memory address is compared to the tag bits associated with the cache lines. This allows checking for cache hits or misses.
* When placing a new block on the cache, as long as the associated cache line is not full, we can place the block anywhere in its cache set. Otherwise, we evict a block from the cache. 

#### Advantages
* Flexible placement of memory block. We can, thus, fully utilize the cache.
* Better placement implies better  hit rate.
* More flexible cache replacement policies can be used on a cache miss.

#### Disadvantages
* Slower placement because we have to iterate through all cache lines.
* More power hungry cache placement.
* Most expensive. 

### Set Associative 
* Cache is divided into $n$ sets, each set contains $m$ cache lines. 
* A memory block is then *mapped to a set and placed into any cache lines in the set. *
* We can represent the associativity with an $n\times m$ matrix
* We say a cache is **$n$-way set associative** if each set contains $n$ blocks.

#### Block Query
1. Determine the set using the index bits derived from the address of the memory block.
2. Use the tag bits to check the cache lines. On a cache hit return the line, otherwise we handle a cache miss.
3. If all cache lines in a set are occupied (for placing data on the cache), we then use our replacement policy.

#### Consequences
* It is a trade-off between [[#Direct-Mapped]] and [[#Fully Associative]] caches.
* It allows the use of a [[#Cache Replacement Policy]]


##  Cache Replacement Policy
* An instruction used to manage the cache when the cache is full and we need to discard some items to make room for others.
### Random Replacement
* Discard items from the cache line at random.

### Least Recently Used Replacement
* Discard least recently used items first.
* This requires us to keep track of an age bit in the cache line to determine how long ago a block was placed.

### Most Recently Used Replacement
* Discard most recently used items first

## Cache Reading Policy
* Dictates what to do when a read operation is performed and it causes a cache miss.
### No Load-Through 
* Information is read from the backing store and a *cache line is copied into the cache*. The data is then transferred from cache to processor.
### Load Through 
* Information is read from the backing store and directly transferred to the processor. It may *optionally fill a cache line*.

## Cache Writing Policy
* Dictates what to do when a write is performed on the cache. In particular, it specifies how to handle ensuring data consistency, and how to handle misses.
### Cache Hit Policies
#### Write Through
* *Writing is done to both cache and backing store*. 
#### Write Back
* *Writing is done only to the cache* The write to the backing store is postponed until the modified content is about to be replaced by another cache block
* *Tends to be more complex* since we need to track which locations have been written over. This means that during a read miss, we require two memory accesses--one to write the replaced data from the cache back to the store, and one to retrieve the data.

### Cache Miss Policies
#### Write Allocate
* Data at the missed write location is *loaded into the cache*, followed by a write hit operation.

#### No-Write Allocate
* Data at the missed location is not loaded into the cache. 
* *Directly write into the backing store.*