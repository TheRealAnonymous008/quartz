* **Dependency Injection** is a design pattern in which an entity receives any entities that it depends on.
# Structure
![[Dependency Injection.png]]<figcaption> Image from: Venderjoe https://commons.wikimedia.org/wiki/File:W3sDesign_Dependency_Injection_Design_Pattern_UML.jpg </figcaption>

# Motivation
1. By using dependency injection we reduce the amount of coupling between entities. An object only needs to know about the interface it depends on.
2. Separation of concerns between how an object is made and how it is used. We offload initialization somewhere else.
3. Modularity in design. Because of a lack of coupling, we can modify the dependencies as needed without having to change the object.
4. Inversion of control
5. Dependency Inversion principle is upheld

# Caveats
1. Abstraction and Indirection obscures details, leading to more difficult to trace code.
2. Trades off the dependency of objects with a dependency to a framework instead (i.e., how we choose to implement the Dependency Inversion pattern)
3. Complexity increases.
4. Slight runtime penalties (although negligible).

# Links
* [[Object Oriented Programming]] - specifically the section on SOLID.
