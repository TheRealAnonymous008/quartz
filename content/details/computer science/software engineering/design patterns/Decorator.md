* *Aka*: Wrapper
* *Intent*: Attach additional responsibilities to an object dynamically, providing a flexible alternative to subclassing for extending functionality.

# Structure
![[Decorator.png]]<figcaption> Image from: Gamma, Helm, Johnson, and Vissides </figcaption>

# Applicability
* Add responsibilities to individual objects dynamically and transparently without affecting other objects.
* Add responsibilities that can be withdrawn.
* Extension by subclassing would result in complex class hierarchies or would be impractical.

# Consequences
* More flexible than static inheritance
* Avoids feature-laden classes high up in the hierarchy, making super classes simpler.
* A decorator and its component aren’t identical. Don’t rely on object identity.
* Lots of little objects, making debugging hard

# Implementation
## Interface conformance: 
* A decorator’s interface must conform to the interface of what it decorates.

## Lightweight classes
* There is no need to define an abstract decorator class when there is only one responsibility to be added
* Focus on defining the component (the parent of decorators and components it decorates) interface.

## Decorators vs [[Strategy]]:
* Strategies are better for heavyweight Components.
* Strategies require modifying components for extensions.