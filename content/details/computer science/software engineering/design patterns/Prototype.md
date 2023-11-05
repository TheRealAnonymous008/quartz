* *Intent*: Specify the kinds of objects to create using a prototypical instance and create new objects by copying this prototype

# Structure
![[Prototype.png]]<figcaption> Image from: Gamma, Helm, Johnson, and Vissides </figcaption>

# Applicability
* When the classes to instantiate are specified at runtime (i.e. dynamic loading).
* A system should be independent of how its products are created, composed, and represented
* Avoid building a class hierarchy of factories that parallels the class hierarchy of products
* When instances of a class can have one of only a few different combinations of states.

# Consequences
* It hides concrete product classes from the client.
* Lets a client work with application-specific classes without modification.
* Adding and removing products at runtime.
* Specifying new objects by varying values.
* Specifying new objects by varying structure
* Reduced subclassing.
* Configuring an application with classes dynamically.
* Each subclass of the Prototype pattern must implement a clone operation, which may be difficult.

# Implementation
* Use a prototype manager: when the number of prototypes in the system isn’t fixed.  The manager acts as a register.
* Implement a clone operation which works. Decide what information needs to be shared.
* Clone methods may require arguments for initialization: introduce an initialization method.
* Beware of deep copying clone operations as copies may have to be deleted.