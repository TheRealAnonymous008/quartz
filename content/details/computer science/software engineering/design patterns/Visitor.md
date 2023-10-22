* *Intent*: Represent an operation to be performed on the elements of an object structure. Lets you define a new operation without changing the classes of the elements on which it operates.
# Structure
![[Visitor.png]]

# Applicability
* An object structure contains many classes of objects with different interfaces and you want to perform operations on these objects that depend on their concrete classes.
* Many distinct and unrelated operations need to be performed in an object structure and you want to avoid polluting their classes with these operations.
* The classes defining the object structure rarely change but you often want to define new operations over the structure.

# Consequences
* Makes adding new operations easy.
* Gathers related operations and separates unrelated ones.
* Adding new element classes is hard.
* Allows traversing through class hierarchies
* Visitors can accumulate state as they visit each element.
* Breaks encapsulation.

# Implementation
## Double Dispatch
* Allows you to add operations without changing them. The operation that gets executed depends on the type of Visitor and the type of elements It visits.

## Responsibility for Traversing Objects
* Could be a function In the object structure
* Could be in the visitor (for complex traversals)
* Could be in a separate [[Iterator]] object