* **Dependency Injection** is a design pattern in which an entity receives any entities that it depends on.
# Structure
![[Dependency Injection.png]]<figcaption> Image from: Venderjoe https://commons.wikimedia.org/wiki/File:W3sDesign_Dependency_Injection_Design_Pattern_UML.jpg </figcaption>

# Motivation
* By using dependency injection we reduce the amount of coupling between entities. An object only needs to know about the interface it depends on.
* Separation of concerns between how an object is made and how it is used. We offload initialization somewhere else.
* Modularity in design. Because of a lack of coupling, we can modify the dependencies as needed without having to change the object.
* Inversion of control
* Dependency Inversion principle is upheld

# Caveats
* Abstraction and Indirection obscures details, leading to more difficult to trace code.
* Trades off the dependency of objects with a dependency to a framework instead (i.e., how we choose to implement the Dependency Inversion pattern)
* Complexity increases.
* Slight runtime penalties (although negligible).

# Links
* [[Object Oriented Programming]] - specifically the section on SOLID.
