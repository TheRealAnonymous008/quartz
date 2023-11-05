* *Intent*: Use sharing to support large numbers of fine-grained objects efficiently.

# Structure
![[Flyweight.png]]
<figcaption> Image from: Gamma, Helm, Johnson, and Vissides </figcaption>

# Applicability
* When all of the following hold:
* An application uses a large number of objects.
* Storage costs are high because of the sheer quantity of objects.
* Most object states can be made extrinsic—i.e. dependent on context.
* Many groups of objects may be replace by relatively few shared objects once extrinsic state is removed.
* The application doesn’t depend on object identity.

# Consequences
* Runtime costs for transferring, finding and computing extrinsic states are offset by saving space.
* More flyweights mean greater storage savings.

# Implementation
## Considerations
* Extrinsic states of the flyweight are computed externally.
* Clients shouldn’t instantiate shared objects

## Retrieval
* Use of a [[Factory Method]] as a [[Facade]] for a constructor for a complex system. There should be a way to retrieve the newly created object from the factory method.
* Typically, we choose to cache this object or to partition and reassemble it before returning.

## Caching
* **Maintained Caches** (i.e., using data structures) are suitable for highly variable states.
* **Unmaintained Caches** are initialized in bulk and take less overhead when initializing objects, at the cost of having more overhead for retrieving cached objects.
* We may use the [[Chain of Responsibility]] to loosely couple multiple caches associated with a complex flyweight.