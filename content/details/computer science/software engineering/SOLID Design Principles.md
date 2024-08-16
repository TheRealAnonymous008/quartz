* Principles towards more maintainable and flexible code.
### Single Responsibility Principle
* A module should be responsible to one and only one actor.
* A class should only have one reason to change. 
	* This "reason" corresponds more to the question of "*who must the design of the code respond to?*" Design the modules to respond to just one business function, and such that each change corresponds to just one module.
* *Gather together the things that change for the same reasons. Separate those things that change for different reasons.
* **Separation of Concerns*** - don't write the program as one entire block. Instead, break it up into distinct chunks that are designed to perform a single, simple task (called a **concern**). This is good because:
	* Less Complexity in the Code
	* More manageable code
	* Modular code
	* Easier to test code.

### Open-Closed Principle
* Objects or entities should be open for extension and closed for modification
* Our entities must allow for us to extend its behavior without modifying any of the existing code.
* Accomplished via inheritance and polymorphism.
* *Note*: *it is impossible for a program to be fully closed*. some part of the code must change if we want to add new functionality). Thus, the designer must choose the changes which the program must be closed to, such that *changes do not necessitate modifying closed code.*
* *Consequences*:
	* Make all member variables private. Public variables may make it so a class is dependent on another class' public variable.
	* Use encapsulation
	* No global variables 
	* *If there are few dependents, we may violate these rules*.

### Liskov Substitution Principle
* Let $q(x)$ be a property provable about objects of $x$ of type $T$.
  
  Then $q(y)$ should be provable for objects $y$ of type $S$ where $S$ is a subtype of $T$.
* *Every derived class must be substitutable to their parent classes* without the function knowing.

### Interface Segregation Principle
* A client should never be forced to implement or depend on an interface it doesn't used. 
* *Segregate interfaces based on specificity*.
* This is good because:
	* *Less coupling*.
	* *More readable*. The interfaces may describe the intent of the piece of software.
	* *Simpler interfaces*. Break down complex interfaces into simpler ones.

### Dependency Inversion Principle
* *Decouple modules based on the following rules*. 
	* High level modules should not depend on low-level modules. Both should depend on abstractions
	* Abstractions should not depend on details. Details should depend on abstractions.
* Interactions between modules in different levels of abstractions should be thought of as *abstract interactions*. They *only expose the necessary behaviors*.
* This has some implications
	* All member variables must be interfaces or abstractions
	* Connect concrete classes through abstractions.
	* Do not derive or override from concrete entities.
	* Use [[The Design Patterns#Creational Patterns|creational patterns]] or [[Dependency Injection]]
* Some drawbacks
	* We may have more bloated if we do not think about what each interface represents.
	* Increased complexity and maintenance cost due to the abstraction obscuring things.
	* More boilerplate code.