* *Intent*: Define an object that encapsulates how a set of objects interact. It promotes loose coupling by keeping objects from referring to each other explicitly, and it lets you vary their interaction independently.
# Structure
![[Mediator.png]]

![[Mediator Object.png]]

# Applicability
* A set of objects communicate in well-defined but complex ways. The resulting interdependencies are unstructured and difficult to understand.
* Reusing an object is difficult because it refers to and communicates with many other objects.
* A behavior that’s distributed between several classes should be customizable without a lot of subclassing

# Consequences
* It limits subclassing.
* It decouples interacting classes (colleagues)
* It simplifies object protocols
* It abstracts how objects cooperate.
* It centralizes control, it can make the mediator itself monolithic.

# Implementation
## Colleague-mediator communication
* Implement the mediator as an [[Observer]]
* Define a specialized notification interface in mediator that lets colleagues be more direct in their communication.