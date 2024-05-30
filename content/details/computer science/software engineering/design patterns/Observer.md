* *Aka:* Dependents. Publish-Subscribe
* *Intent*: Define a one-to-many dependency between objects so that when one object changes state, all its dependents are notified and updated automatically.

# Structure
![[Observer.png]]<figcaption> Image from: Gamma, Helm, Johnson, and Vissides </figcaption>

# Applicability
* When an abstraction has two key aspects: one dependent on the other.
* When a change to one object requires changing others and you don’t know how many objects need to be changed.
* When an object should be able to notify other objects without making assumptions about who these objects are.

# Consequences
* Lets you vary subjects and their observers independently.
* Abstract coupling between subject and object
* Support for broadcast communication.
* Freedom for adding and removing observers
* Observers can be blind to the cost of updates

# Implementation
## Subject-Observer Mapping
* Use associative look up ([[Hashed Data Structure|Hash tables]] tables) if space is an issue
* Store references to observers in the subject if time is an issue

## Multiple subjects
* If more than one subject is to be observed, the observer should know which subject is changing. Achieved by passing subject as parameter for update.

## Update Triggers
* Have state-setting operations on subject notify all observers (client doesn’t need to remember to notify observers, but consecutive operations may be inefficient)
* Make clients responsible for calling Notify at the right time (avoids unnecessary intermediate updates at the cost of the client having the responsibility to notify observers)

## Handling Dangling Subject References
* Make subject notify observers as it is deleted

## Ensuring State Invariance
* Send notifications from a template method

## Avoid observer specific update protocols
* **Push-model** – subject sends observers detailed information about the change (makes code less reusable due to assumptions that may not be true).
* **Pull model** – the subject sends nothing but the most minimal notification and observers ask for details (inefficient)

## Update Efficiency
* Improve update efficiency by specifying modifications of interest explicitly.
* Use a change manager ([[Singleton]] and [[Mediator]]) for complex update semantics to minimize the work required to update observers.. The change manager is responsible for:
	* Mapping subject to observers
	* Define update strategies
	* Updates all observers upon request.
