# Four Principles

### Abstraction
* Generalize details. Abstraction serves to separate or *hide the implementation details from the intended usage of a thing*
* Aim for transparency
	* A system is **transparent** if the user has no idea about the details of the system.
	* **Interface** - a construct that exposes certain behaviors to a client, while hiding the server's implementation. 

### Encapsulation
* Bundle the data with the mechanisms that operate on the data.  
* We restrict access to an entity's components, and we include methods that can operate on these data. 
* **Defensive Copying'** - If the mutable object's field's state should be changed only by its owner, then we make copies of this object any time it's passed into or out of the class.
	* This enforces encapsulation for the object so that the caller cannot see the actual mutable object held by the class.

### Inheritance
* The mechanism of *basing a class on another class*, allowing us to retain similar behaviors to these classes, while at the same time adding new implementations.
* We refer to one class as the **superclass** and the class that inherits from it as the **subclass**.

### Polymorphism
* **Polymorphism** - a technique where we represent entities of different types using a single interface. 

* **Ad-hoc Polymorphism*** - a variant of polymorphism wherein functions can be *applied to arguments of different types* because a polymorphic function can denote a number of distinct and potentially heterogeneous implementations depending on the type of arguments.
	* This translates to operator overloading or function overloading.
* **Parametric Polymorphism** - allows a single piece of code to be *given a generic type* using variables in place of actual types. These types are then instantiated as needed.
* **Subtyping** - polymorphism in which a subtype is a data type that is related to another data type by some notion of [[#Liskov Substitution Principle|substitutability]]

# Cohesion and Coupling
* **Cohesion** refers to the degree to which elements inside a module belong together. 
* **Coupling** pertains to the degree to which different modules in an application are interdependent. 

* *A highly cohesive system is desirable* since it is more readable and easier to maintain.
* *A loosely coupled system is desirable* to make the system more modular and easier to extend.
* We increase cohesion when
	1. The functionalities embedded in a class, accessed via methods, have much in common.
	2. Methods can carry out a small number of activities. They do one thing.
	3. Related methods are grouped together.

### Levels of Cohesion
* **Coincidental Cohesion** - when parts of a module are *grouped arbitrarily*, with the only relationship they have is that they are grouped together. 
* **Logical Cohesion** - when parts of a module are grouped together because they are *logically categorized into the same thing* even though they are different by nature 
	* *Example*: Grouping all input handlers together because they handle input.)
* **Temporal Cohesion** - when parts of a module are grouped by *when they are processed.*
* **Procedural Cohesion** - when parts of a module are grouped because they always *follow a certain sequence of execution*. That is, one part follows the next in a well defined order.
* **Informational Cohesion** - when parts of a module are grouped because they *operate on the same data.*
* **Sequential Cohesion** - when parts of a module are grouped because the output from one part is the input to another part like an assembly line. There is a *well defined sequence for the dependencies* of each component.
* **Functional Cohesion** - when parts of a module are grouped together because they *all contribute to a single well defined task* of the module
# SOLID
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