* *Intent*:  Separate the construction of a complex object from its representation so that the same construction process can create different representations.
# Structure
![[Builder.png]]

# Applicability
* The algorithm for creating a complex object should be independent of the parts that make up the object and how they’re assembled.
* The construction process must allow different representations for the object that’s constructed

# Consequences
* It lets you vary a product’s internal representation
* It isolates code for construction and representation.
* It gives you finer control over the construction process

# Implementation
* Assembly and construction interface: the builder interface should be general enough to be used by all concrete builders.
* Tree structures can be used to access parts constructed earlier.
* The products differ so greatly that there is little to gain from creating abstract classes for products.
* Set empty methods as default methods in the builder interface.
