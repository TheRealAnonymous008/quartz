* *Intent*: Used when an object is to be instantiated many times to the point that it causes significant overhead

# Structure
![[Object Pool.png]]
<figcaption> Object Pooling. Image taken from GeeksforGeeks  </figcaption>

# Applicability
* You want to allocate and deallocate many object instances. 
* When you want to have a limited number of said objects at a time (i.e., an extended version of a [[Singleton]]).

# Consequences 
* It reduces the overhead for allocating the objects since they are simply fetched from the pool when needed and returned to the pool when done. 
* The pooled object is obtained in a predictable time. 
* In some cases, the memory overhead of storing pre-allocated resources may be quite high. 
* Garbage Collectors may render them redundant or even an anti-pattern. 

# Implementation
* In the case when the pool is empty we have three options 
	* Throw an error (useful when only a bounded amount of the resource may exist)
	* The pool can simply create a new instance of that object. 
	* The pool may block other clients (in a [[Multiprogramming]] context) until a thread frees its object.
* The client must request an object from the pool via its factory method. 
* When the object is returned to the pool, it must be reset to an original state in some way. 