* *Aka*: Action, Transaction
* *Intent*: Encapsulate a request as an object, thereby letting you parameterize clients with different requests, queue or log requests, and support undoable operations.
# Structure
![[Command.png]]
<center> Image from: Gamma, Helm, Johnson, and Vissides </center>

# Applicability
* Parameterize objects by an action to perform
* Allow replacement to function callbacks
* Specify, queue and execute requests at different times.
* Support undoing of commands.
* Support logging changes so they can be reapplied in case of a system crash.
* Structure a system around a high level operations built on primitive operations

# Consequences
* Command decouples the object that invokes the operation from the one that knows how to perform it.
* Commands can be encapsulated and extended.
* You can assemble commands into a [[Composite]] command.
* It’s easy to add new commands because you don’t have to change existing classes.

# Implementation
## How intelligent should a command be?
* The command defines a binding between a receiver and the actions that carry out the request.
* The command implements everything itself without delegating to a receiver., useful when a command should be independent of existing classes or when no receiver exists or when a command knows its receiver implicitly.

## Undoing and Redoing Commands
* Supporting undo and redo by keeping an undo function in the Command class, and a history class.
* Avoiding error accumulation in the undo process. Ensure commands can store the original state of objects.