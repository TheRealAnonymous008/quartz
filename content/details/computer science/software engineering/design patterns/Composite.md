* *Intent*: Compose objects into tree structures to represent part-whole hierarchies and let clients treat individual objects and compositions uniformly
# Structure
![[Composite.png]]

![[Composite Tree.png]]
# Applicability
* You want to represent part-whole hierarchies of objects.
* You want clients to ignore the differences between compositions of objects and individual objects.

# Consequences
* Defines class hierarchies consisting of primitive objects and composite objects.
* Makes the client simple as composites and primitives are treated the same.
* Makes it easier to add new kinds of components.
* Can make the design overly general. Making it so only certain components are present is difficult.

# Implementation
## Parent References
* Simplifies the traversal from parent to leaf 
* Define the parent reference in the Component class.
* Change the parent of the component only when it is being added or removed.

## Sharing components
* Children can store multiple parents, but this can lead to ambiguities.

## Use Common Denominators
Maximize component interface by defining as many common operations for Composite and Leaves.

## Declaring child management operations
* Declare operations in the component which are inherited by the leaves (more transparent but less safe)
* Declare operations in the composites (safer but less transparent due to differing interfaces)
* Declare an operation to convert a component to a composite.

## Considerations 
* Implementing a list of children in the base class incurs a space penalty for every leaf.
* Children can be ordered
* Caching to save time in search and traversal.
* Consider who should delete components (usually best to make the component responsible for deleting its children).
* Use data structures