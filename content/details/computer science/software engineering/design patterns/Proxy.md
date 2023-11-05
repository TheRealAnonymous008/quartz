* *Aka*: Surrogate
* *Intent*: Provide a surrogate or placeholder for another object to control access to it
# Structure
![[Proxy.png]]
<center> Image from: Gamma, Helm, Johnson, and Vissides </center>


![[Proxy (Runtime).png]]
<center> Image from: Gamma, Helm, Johnson, and Vissides </center>

# Applicability
* Applicable when there is a need for a more versatile or sophisticated reference to an object than a pointer

# Types
## Remote
* Provides a local representative for an object in a different address space.

## Virtual
* Creates expensive objects on demand.

## Protection
* Controls access to the original object (i.e. if objects should have different access rights

## Smart reference 
* Performs additional actions when an object is referenced such as
* Loading a persistent object into memory when first referenced
* Counting the number of references to the real object so it can be freed when there are no more references.
* Checking the real object is locked so no object can access it

# Consequences
* Introduces a level of indirection when accessing an object:
	* Remote proxies hide that an object resides in a different address space
	* Virtual proxies perform optimizations
	* Protection and Smart proxies allow housekeeping tasks on access.
* Postponing the copy process to reduce its cost.

# Implementation
* Exploit overloading operators such as -> in C++.
* Proxy doesn’t always have to know the type of the subject (unless the proxy is a virtual proxy)
* Consider how clients will refer to subjects before they are instantiated.