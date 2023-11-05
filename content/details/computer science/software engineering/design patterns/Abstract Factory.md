* *Aka*: Kit.
* *Intent*: Provide an interface for creating families of related or dependent objects without specifying their concrete classes
# Structure
![[Abstract Factory.png]]
<figcaption> Image from: Gamma, Helm, Johnson, and Vissides </figcaption>

# Applicability
* A system should be independent of how its products are created, composed, and represented.
* A system should be configured with one of multiple families of products.
* A family of related product objects is designed to be used together and you need to enforce this without constraint.
* You want to provide a class library of products and you want to reveal their interfaces, not their implementations

# Consequences
* It isolates concrete classes.
* It makes exchanging product families easy
* It promotes consistency among products.
* Supporting new kinds of products is difficult.

# Implementation
## Implement a [[Factory Method|Factory]] as a singleton.

## Creating the product:
* Define a factory method for each product.
* Implement using the [[Prototype]] patterns if many product families are possible.

## Defining Extensible Factories:
* Define a different operation for each kind of product; this requires changing the Abstract Factory.
* Add a parameter to operations that create objects to specify the kind of object created; more flexible, less safe.