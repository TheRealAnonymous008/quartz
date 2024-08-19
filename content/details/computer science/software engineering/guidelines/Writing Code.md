## Class Design
* Use **Abstract [[Data Structures|Data Types]]**. The benefits of using ADTs are that:
	* We can hide implementation details.
	* Changes to implementation don't affect the whole program.
	* The interface for the class can be more informative.
	* Optimization is easier.
	* The program is more readable and more obviously correct.
	* The program becomes more self-documenting
	* Low fan-out. Data is passed in a pre-defined way and it is easy to modify how the data is passed without modifying the rest of the code.
	* It is easier to work with real-world entities (what ADTs represent) than low-level implementation structures. There is better abstraction, and less [[Cohesion and Coupling|coupling]].
\
* If the language does not support the making of ADTs we need to consider the following:
	* Add services for creating and deleting instances.
	* Add services for mutating the instance.
	* For the ADT interface consider the following options
		* Identify instances (i.e., via objectID) each time an ADT service is used. 
		* Explicitly provide the data used by the ADT services. It removes the need for lookup based on an identifier at the cost of exposing data. It becomes tempting to modify information that should be kept secret.
		* Design a service to make a specific ADT instance the current one. All services use the current font. This is more streamlined but less applicable for complex applications.

* *Good ADTs require Good [[Object Oriented Programming|classes]] Interfaces with Good Abstraction*
	* Present a consistent level of abstraction in the class interface. Each class implements one and only one ADT. 
		* The ADT should be obvious just from looking at the class. 
		* When you mix levels of abstraction you introduce **leaky abstractions** that makes the program harder to understand
	* Be sure you understand what abstraction the class is implementing. When you have to choose between two similar abstractions, make sure you choose the right one.
	* Most operations have corresponding equal and opposite operations. Check to see if you need it.
	* Move unrelated information to another class. If the majority of routines work with half of the data in the class, split the class.
	* Make interfaces programmatic rather than semantic. This means that as much as possible -- the assumptions in the interface is enforceable by the compiler.
		* Do not rely on an order of operations (i.e. $X$ must happen before $Y$)
		* If you rely on a semantic ordering, document it in code.
		* *Any aspect that can't be enforced by the compiler is an aspect that's likely to be misused.*
		* Use asserts to convert semantic assumptions to programmatic assumptions.
	* Beware of erosion of the interface's abstraction under modification. If you have to add more to the class, consider splitting it.
	* Don't add public members that are inconsistent with the abstraction. Preserve the integrity of the abstraction.
	* Consider abstraction and cohesion together. *A consistent abstraction gives rise to strong cohesion*

* *Enforce encapsulation to support abstraction*
	* Minimize accessibility of classes and members. Favor the strictest level of privacy that's workable (i.e., private). *Prefer to hide than to expose*
	* Don't expose member data in public.
	* Avoid putting private implementation details into a class's interface. [^impl]. *[[SOLID Design Principles|separate the interface]] from the implementation*
	* Don't make assumptions about the class's users.
	* Avoid friend classes (exception being the [[State]] pattern)
	* Don’t put a routine into the public interface just because it uses only public routines. The interface should only contain methods relevant to the abstraction.
	* Favor read-time convenience to write-time convenience. *Code is read far more than it is written*
	* *Be wary of violations to semantic encapsulation*
		* Anytime you find yourself looking at a class’s implementation to figure out how to use the class, you’re not programming to the interface; you’re programming through the interface to the implementation
		* When you don't understand how to use the interface, do not look at its implementation. If you are responsible for that code, modify only the interface or its documentation
	* Watch for coupling that is too tight.
		* Minimize accessibility of classes and members
		* Avoid friend classes. They are automatically tightly coupled.
		* Prefer private rather than protected data.
		* Avoid exposing member data in a class's public interface.
		* Be wary of semantic violations to encapsulation
		* Observe the Law of Demeter

[^impl]: This also discourages programmers from reading through the "private" section of a class. This boils down to making sure the interface is public only. Anything else should be contained in an internal class.

* Represent "has a" relationships through containment (i.e., $A$ has an instance of $B$)
	* "Has a" relationships should be done via private inheritance only as a resort (and even then it should be changed to a better design later).
	* If a class contains more than seven members, decompose it

* Represent "is a" relationships through inheritance.
	* Inheritance helps avoid the need to repeat code and data in multiple locations by centralizing it within a base class.
	* Inheritance should be public by default. 
	* If the derived class isn’t going to adhere completely to the same interface contract defined by the base class, inheritance is not the right implementation technique
	* Remember: *Inheritance adds complexity. Design and document for inheritance or prohibit it (i.e., make the class uninheritable)* 
	* All the routines defined in the base class should mean the same thing when they’re used in each of the derived classes [^LSP].
	* Be sure to inherit only what you inherit. Inherited routines should only be the following:
		* **Abstract Overridable** - the derived class inherits the interface but not the implementation
		* **Overridable** - the derived class inherits the interface and a default implementation and is allowed to override the default implementation
		* **Non-Overridable** - the derived class inherits the interface and its default routine, and is not allowed to override the implementation.
	* *If you want to use a class’s implementation but not its interface, use containment rather than inheritance. Do not inherit if you do not intend to use the interface*. 
	* Do not override non-overridable member functions. Do not reuse names of non-overridable base class routines in derived classes.
	* Move common interfaces, data and behavior as high as possible in the inheritance tree. If you find that moving them breaks the higher object's abstraction, you can stop.
	* Aside from [[Singleton]], be suspicious of classes with only one instance.
	* Be suspicious of base classes of which there is only one derived class. *This is a sign of anticipating future needs that may not arise*
	* Be suspicious of classes that override a routine and do nothing inside the derived routine. It adds complexity and makes code hard to read and maintain. *This is a sign that the base class's abstraction does not capture the object it is modelling*. 
	* Avoid deep inheritance. Deep inheritance minimizes complexity.
	* Prefer polymorphism to extensive type checking.
	* Make all data private not protected. If the data is needed, provide accessor functions instead.
	* Beware of using multiple inheritance. It can add complexity
		* Exception: Mixins that are used to customize class behavior (i.e., they allow properties to be mixed in as needed). For as long as mixins are truly independent of each other.

[^LSP]: This is another way of saying -- -adhere to the Liskov Substitution Principle

* Consider the following rules of thumb for Containment vs Inheriitance
	* If multiple classes share common data but not behavior, create a common object that those classes can contain.
	* If multiple classes share common behavior but not data, derive them from a common base class that defines the common routines.
	* If multiple classes share common data and behavior, inherit from a common base class that defines the common data and routines.
	* *Inherit when you want the base class to control your interface; contain when you want to control your interface.*

* The following guidelines help for member functions and member data
	* Keep the number of routines in a class as small as possible.
	* Disallow implicitly generated member functions and operators you don't want.
	* Minimize the number of different routines called by a class
	* Minimize indirect routine calls to other classes. Follow the Law of Demeter.
	* Minimize the extent to which a class collaborates with other classes. Minimize all of the following
		* Number of kinds of objects instantiated
		* Number of different direct routine calls on instantiated objects
		* Number of routine calls on objects returned by other instantiated objects
	* Initialize all member data in the constructor if possible.
	* Enforce singleton using a private constructor.
	* Prefer deep copies to shallow copies until proven otherwise.
		* Deep copies are often simpler to code and maintain than shadow copies.
		* Shallow copies are prone to exposing data to classes that might mutate them incorrectly.

* *Know why you're creating a class*. The following are good reasons for it.
	* To model real-world objects
	* To model abstract objects
	* To [[Software Design|minimiize the complexity]] of the program through abstraction of details.
	* To isolate complex implementation
	* To hide implementation details.
	* To limit the effects of changes. Design so that areas that are most likely to change are the easiest to change
	* To hide global data and its implementation.
	* To streamline parameter passing, especially when the volume of data is large.
	* To make a central point of control and a single source of truth.
	* To facilitate reusable code.
		* *Prevent prematurely creating functionality you do not need by having a project at the end / start of the sprint to make the code reusable*. 
	* To plan for a family of programs which may change certain details.
	* To package related operations.
	* To refactor the code.

* Do not create **god classes** that retrieve data from other classes.
* Do not create classes with only data but no behavior. *Remember classes model behavior*
* Name all classes after nouns

* *If the language does not support class structures, enforce it through coding standards* 

## Routine Design

# Links
* [[Code Complete by McConnell]] - Ch. 6 ,7
* [[Clean Code Principles]] - additional guidelines on writing code are presented.