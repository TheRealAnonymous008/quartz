* *Aka*: Token
* *Intent*: Without violating encapsulation, capture and externalize an object’s internal state so that the object can be restored to this state later

# Structure
![[Memento.png]]
<center> Image from: Gamma, Helm, Johnson, and Vissides </center>

# Applicability
* A snapshot of an object’s state must be saved so that it can be restored to that state later.
* A direct interface to obtaining the state would expose implementation details and break encapsulation.

# Consequences
* Preserving encapsulation boundaries.
* It simplifies the originator by having storage management be on another class.
* Using mementos might be expensive if the originator class must copy large amounts of information.
* Defining narrow and wide interfaces might be difficult.
* An otherwise lightweight memento caretaker incurs hidden costs for storing since it doesn’t know how much data is in the memento.

# Implementation
* Store incremental changes when mementos get created and passed back to the originator’s original state.