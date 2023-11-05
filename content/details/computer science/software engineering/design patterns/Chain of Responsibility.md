* *Intent*: Avoid coupling the sender of a request to its receiver by giving more than one object a chance to handle the request. Chain the receiving objects and pass the request along the chain until an object handles it.

# Structure
![[Chain of Responsibility.png]]
<center> Image from: Gamma, Helm, Johnson, and Vissides </center>

# Applicability
* More than one object may handle a request and the handler isn’t known a priori.
* The handler should be ascertained automatically
* You want to issue a request to one of several objects without specifying the receiver explicitly.
* The set of objects that can handle a  request should be specified dynamically

# Consequences
* Reduced coupling simplifies object interconnections.
* Added flexibility in assigning responsibilities to objects
* Receipt isn’t guaranteed since a request has no explicit receiver

# Implementation
## Successor Chain Implementation
* Define new links usually in Handler classes
* Use existing links when they work well to support the needed chain.

## Connecting successors
Introduce pre-existing references if there aren’t any. Handlers will maintain their successors.

## Representing requests
* Safe approach: Use Hard-coded operation invocation.
* Use a single handler function that takes a request code, represented as request objects,  as parameter (open ended and more flexible)