* *Aka*: Virtual Constructor
* *Intent*: Define an interface for creating an object, but let subclasses decide which class to instantiate. It lets a class defer instantiation to subclasses
# Structure
![[Factory Method.png]]<figcaption> Image from: Gamma, Helm, Johnson, and Vissides </figcaption>

# Applicability
* A class can’t anticipate the class of objects it must create
* A class wants its subclasses to specify the objects it creates.
* Classes delegate responsibility to one of several helper subclasses and you want to localize the knowledge of which helper subclass is the delegate

# Consequences
* Eliminates the need to bind application-specific classes in code.
* Clients might have to subclass the Creator class to create a particular concrete product.
* Provides hooks for subclasses
* Connects parallel class hierarchies.

# Implementation
## Manipulators 
Use a Manipulator object to handle interactions between factory objects and handle parallel class hierarchies.

## Variants
* The Creator class is an abstract class and doesn’t have a factory method implementation
* The Creator class is concrete and provides a default factory method implementation.

## Handling Multiple Products
* Parameterized factory methods to create multiple kinds of products.