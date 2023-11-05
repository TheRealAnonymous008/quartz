* *Intent*: Allow an object to alter its behavior when its internal state changes. The object will appear to change its class
# Structure
![[State.png]]
<center> Image from: Gamma, Helm, Johnson, and Vissides </center>

# Applicability
* An object’s behavior depends on its state and it must change its behavior at run time depending on that state.
* Operations have large, multipart conditional statements that depend on the object’s state. (often represented as an enum).

# Consequences
* It localizes state-specific behavior and partition behavior for different classes.
* New states can easily be added
* Increases the number of classes depending on the number of states.
* Makes state transitions explicit
* State objects can be shared

# Implementation
## Who defines State Transitions?
* If the criteria are fixed, it can be done on the context.
* It is more flexible to let state subclasses to specify their successor state. (introduces dependencies between classes)

## Creating and Destroying State Objects
* Create state objects only when they’re needed and destroy them afterwards (states aren’t known at run time and contexts change frequently)
* Create states ahead of time and never destroy them (state changes occur rapidly and storage isn’t an issue)
