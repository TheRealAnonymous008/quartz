* *Aka*: Policy
* *Intent*: Define a family of algorithms, encapsulate each one and make them interchangeable. It lets the algorithm vary independently from clients that use it.
# Structure
![[Strategy.png]]
<center> Image from: Gamma, Helm, Johnson, and Vissides </center>

# Applicability
* Many related classes differ only in their behavior.
* You need different variants of an algorithm
* An algorithm uses data that clients shouldn’t know about.
* A class defines many behaviors and these appear as many conditional statements.

# Consequences
* Defines a family of algorithms for contexts to reuse. Inheritance can factor out common functionalities.
* An alternative to subclassing, especially for classes differing only in behavior
* Eliminates conditional statements.
* Provides a choice of implementations for the same behavior
* Clients must be aware of different Strategies before it can select the appropriate one.
* Communication overhead between strategy and context.
* Increased number of objects.

# Implementation
* Use only when the variation is behavior irrelevant to clients.

## Defining Strategy and Context interfaces. 
The strategy and context must provide each other efficient access to needed data:
	* Have context pass data in parameters (decouples Strategy and context, but context might pass unneeded data).
	* Store a reference to context in Strategy (or have context pass itself as parameter) (tightly couples Strategy and context, but strategy can request exactly what it needs)

## [[Template Method|Template Methods]]
Strategies as template parameters if: the Strategy can be selected at compile-time and it doesn’t have to be changed at run time.

## Optional Strategy Objects
* Remove strategy objects in contexts if they aren’t needed or If default behaviors are sufficient.