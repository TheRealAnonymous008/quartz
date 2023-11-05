* *Aka*: Wrapper 
* *Intent*: Convert the interface of a class into another interface clients expect. It lets classes work together that couldn’t otherwise because of incompatible interfaces.
# Structure
## Variations
* **Class Adapter** - Use of polymorphic interfaces which define the contracts that an adapter must adapt by. The adapter then inherits from these interfaces.
![[Class Adapter.png]]<figcaption> Image from: Gamma, Helm, Johnson, and Vissides </figcaption>


* **Object Adapter** - the adapter maintains an instance of the class it is wrapping (like a [[Decorator]]).
![[Object Adapter.png]]<figcaption> Image from: Gamma, Helm, Johnson, and Vissides </figcaption>

# Applicability
* You want to use an existing class, and its interface does not match the one you need.
* You want to create a reusable class that cooperates with unrelated or unforeseen classes, that is classes don’t necessarily have compatible interfaces.
* (Object adapter) You need to use several existing subclasses, but it’s impractical to adapt their interface by subclassing every one. An adapter can adapt the interface of its parent class.

# Consequences
## Class adapter
* Adapts adaptee to target by committing to a concrete abstract class. Hence it won’t work for adapting subclasses.
* Lets adapter override some of adaptee’s behavior
* Introduces only one object and no pointer indirection is needed to get the adaptee

## Object adapter
* Lets a single Adapter work with many Adaptees
* Makes it harder to override adaptee behavior.

## In general:
* Adapters can adapt many adaptees
* Interface adapters let us incorporate our class into systems that expect different interfaces to the class.
* Two way adapters provide transparency from the target to the adaptee and back.

## Implementation
### Use pluggable adapters
Find the smallest subset of operations that let us do the adaptation (narrow interface). Then use any of the following:
* Define abstract operations for the narrow adaptee interface.
* Use delegate objects to forward requests
* Parameterize the adapters