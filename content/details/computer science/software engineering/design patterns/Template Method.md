* *Intent*: Define the skeleton of an algorithm in an operation, deferring some steps to subclasses. It lets subclasses redefine certain steps of an algorithm without changing its structure

# Structure
![[Template Method.png]]<figcaption> Image from: Gamma, Helm, Johnson, and Vissides </figcaption>

# Applicability
* Implement the invariant parts of an algorithm once and leave it up to subclasses to implement behavior they can vary
* When common behavior among subclasses should be factored localized in a common class to avoid code duplication.
* Control subclasss extensions

# Consequences
* Allows factoring out common behavior.
* Lead to an inverted control structure where the parent class calls the operations of a subclass.
* Hook operations (which may be overridden) and abstract operations (which must be overridden) must be distinguished.

# Implementation
* Use access controls so primitive operations can only be called by the template method.
* Minimize primitive operations
