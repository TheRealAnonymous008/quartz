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


# Topics
* [[SOLID Design Principles]]
* [[Cohesion and Coupling]]

# Links
* [[Programming]]