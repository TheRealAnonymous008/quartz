* **Cohesion** refers to the degree to which elements inside a module belong together. 
* **Coupling** pertains to the degree to which different modules in an application are interdependent. 

* *A highly cohesive system is desirable* since it is more readable and easier to maintain.
* *A loosely coupled system is desirable* to make the system more modular and easier to extend.
* We increase cohesion when
	1. The functionalities embedded in a class, accessed via methods, have much in common.
	2. Methods can carry out a small number of activities. They do one thing.
	3. Related methods are grouped together.

# Levels of Cohesion
* **Coincidental Cohesion** - when parts of a module are *grouped arbitrarily*, with the only relationship they have is that they are grouped together. 
* **Logical Cohesion** - when parts of a module are grouped together because they are *logically categorized into the same thing* even though they are different by nature 
	* *Example*: Grouping all input handlers together because they handle input.)
* **Temporal Cohesion** - when parts of a module are grouped by *when they are processed.*
* **Procedural Cohesion** - when parts of a module are grouped because they always *follow a certain sequence of execution*. That is, one part follows the next in a well defined order.
* **Informational Cohesion** - when parts of a module are grouped because they *operate on the same data.*
* **Sequential Cohesion** - when parts of a module are grouped because the output from one part is the input to another part like an assembly line. There is a *well defined sequence for the dependencies* of each component.
* **Functional Cohesion** - when parts of a module are grouped together because they *all contribute to a single well defined task* of the module

# Criteria for Coupling
* Consider the following criteria for coupling
	* *Size* - the number of connections between modules. Minimize size.
	* *Visibility* - the prominence of the connection between two modules. Maximize visibility.
	* *Flexibility* - how easy can you change the connections between modules. Maximize flexibility.

* The most common kinds of coupling are as follows.
	* **Simple Data Parameter Coupling** - all data passed between modules are primitive data types. All data is passed via parameter lists.
	* **Simple Object Coupling** - one object instantiates the other object.
	* **Object Parameter Coupling** - $X$ requires $Y$ to pass it a $Z$. This is a tight coupling.
	* **Semantic Coupling** - one module makes use of some semantic knowledge of another module's inner workings. This should be avoided.

# Links
* [[Code Complete by McConnell]] - Ch. 5