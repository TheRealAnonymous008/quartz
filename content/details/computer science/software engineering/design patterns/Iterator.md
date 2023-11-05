* *Aka*: Cursor
* *Intent*: Provide a way to access the elements of an aggregate object sequentially without exposing its underlying representation.

# Structure
![[Iterator.png]]
<center> Image from: Gamma, Helm, Johnson, and Vissides </center>

# Applicability
* There is a need to access an aggregate object’s contents without exposing its internal representation.
* Support multiple traversals of aggregate objects.
* Provide a uniform interface for traversing different aggregate structures

# Consequences
* It supports variations in the traversal of an aggregate.
* Iterators simplify the aggregate interface.
* More than one traversal can be pending on an aggregate

# Implementation
## Iteration Controllers
* **External iterators** – client controls the iterator. More flexible
* **Internal iterator** – the iterator controls the iteration. Easier to use.

## Traversal Algorithm
* The aggregate defines the traversal algorithm and a client invokes the next operation to change the state of the iterator
* The iterator is responsible for traversal. This is not viable if private variables need to be accessed

## Robustness
* If the list is modified while it is traversed, at the cost of memory, copy the aggregate and traverse the copy.
* Use robust iterators to ensure insertions and removals won’t interfere with traversal. One solution: register the iterator with the aggregate, on modification, the aggregate adjusts the iterator’s state or it maintains information internally.
* Make additional iterator operations according to use.
* Iterators may have privileged access. Make iterators friends of the aggregate if possible, and include protected operations for subclassing.

## Integration with [[Composite|composites]]
* Use an external iterator
* If the composite has an interface for traversal, then keeping track of the current node in the composite is better.
* Use **Null Iterators** to handle boundary conditions on empty objects by ensuring it is always done.