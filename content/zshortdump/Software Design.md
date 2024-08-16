* **Software Design** means the conception, invention, or contrivance of a scheme for turning a specification for computer software into operational software
	* A good top-level design provides a structure that can safely [[Pattern Structure|contain]] multiple lower-level designs
* Software Design is governed by the underlying system [[Upstream Prerequisites and Planning|architecture]]

* The finished software design should look well organized and clean, but the process used to develop the design isn’t nearly as tidy as the end result.

# The Imperative of Software Design
* *The primary imperative of software design is to manage the complexity of the software. 
	* At it essence, software development consists of working out all the details of a highly intricate, [[System Science|interlocking]] set of concepts. 
	* The complexity of the real world is the root of all problems in software design
	* Write code that is easy for the entire team to understand. This means that productivity doesn't grind to a halt because no one understands the code.

* Due to cognitive load associated with storing information about the software, The goal is to minimize the amount of a program you have to think about at any one time. *Minimize essential complexity that arises because of the problem domain*
* *Keep accidental complexity from proliferating*

* We want to design software with the following complexity.
	* Minimal complexity.
	* Ease of maintenance.
	* Loose [[Cohesion and Coupling|coupling]] -- subsystems should only communicate on a need-to-know basis.
	* Extensibility without damaging the existing system.
	* Reusability of system parts to other systems.
	* High fan-in - that is, having many classes use a given class.
	* Low-to-medium fan-out - a given class uses a low-to-medium number of classes.
	* Portability -- it should be easy to move to another environment.
	* Leanness -- the system has no extra parts.
	* Stratification -- design the system so you can view one level without dipping to other levels.
	* Use standard techniques.

* Because design is nondeterministic, skillful application of an effective set of [[#Design Heuristics]] is the core activity in good software design

# Design Heuristics
## Heuristics on Design Attributes
* **Find Real World Objects** - *Use metaphors for complex systems*
	* What are the objects and their attributes (classes and data). What real-world attributes are important for the software.
	* What can be done to each object
	* What can each object do to other objects
	* What parts of the object are visible or invisible to other objects.
	* What is each object's public interface

* **Form Consistent Abstractions** 
	* A good class interface is an abstraction that allows you to focus on the interface without needing to worry about the internal workings of the class.
	* *Abstraction lets you ignore irrelevant details*

* **Encapsulate Implementation Details** *Encapsulation forbids you from looking at the complexity when you don't need to.*

* **Inheritance and Polymorphism** - *Factor out complexity to make things simpler*. These principles simplify programming because we can generalize how we handle anything that depends on an class's general properties and then write specific routines to handle specific operations on specific instances of that class.

* **Information Hiding** - *Hide complexity*.
	* Each class has design or construction decisions hidden from another class.
	* Changes should not ripple to a class's secrets. Hiding information means that the effects of changes are localized.
	* The interface of a class reveals as little as possible about its inner workings.
	* Beware of using the following techniques as they interfere with information hiding.
		* Excessive distribution of information throughout the system. *Centralize information to one source of truth rather than decentralize it*
		* Use of circular dependencies or other dependency loops.
		* Mistaking class data for global data. The real problem is that routines that operate on global data do not know the other routines operating on it nor do they know what happens to the global data.
		* Avoiding performance penalties. Hiding information is not mutually exclusive to performance. This falls under premature optimization.
	* *Thinking about information hiding inspires and promotes design decisions that thinking about objects does not.*

* **Identify Areas Likely to Change** - isolate unstable areas so that the effect of a change is limited to one routine. 
	* The general flow of this heuristic is as follows
		* Identify items that seem likely to change.
		* Separate items that are likely to change.
		* Isolate items that seem likely to change.
	* Also included in things that are likely to change is any difficult design areas. They may be poorly done. Iterating upon them will be easier if we separate them.
	* *Identify the core of the system that makes a minimum viable product*. Anything else is an incremental add-on which may change.

* **Anticipate Different Degrees of Change** - design the system so that the effect or scope of the change is proportional to the chance that the change will occur.  
	* Good designers *also factor in the cost of anticipating change*. If a change is not terribly likely but easy to plan for, you should think harder about anticipating it than if it isn’t very likely and is difficult to plan for.

* **Keep Coupling Loose** - The goal is to create classes and routines with small, direct, visible, and flexible relations to other classes and routines
	* Good coupling between modules is loose enough that one module can easily be used by other modules.
	* Minimize dependencies between modules.
	* See more [[Cohesion and Coupling|here]]

* **Aim for Strong Cohesion** - The more centralized a class becomes in its role, the more you can remember what it does

* **Build Hierarchies** - Hierarchies help organize information better into levels of detail.

* **Formalize Class Contracts** - The object can, in theory, ignore any non-contractual behavior. The contract is dictated by the interface.

* **Assign Responsibilities** - ask what each object should be responsible for (see [[SOLID Design Principles#Single Responsibility Principle|SRP]]). 

* **Design for Test** - design for test results in more formalized class interfaces.

* **Avoid Failure** - look for ways that the system can fail.

* **Choose Binding Time Consciously** - early binding time tends to be simpler but less flexible. 

* **Make Central Points of Control** - there should be One Right Place to look for any nontrivial piece of code, and One Right Place to make a likely maintenance change

* **When in Doubt, use Brute Force** - a dumb solution is better than a complex, elegant one that only works some of the time.

* **Use Diagrams**

* **Keep design Modular** - think of the system as a series of interconnected black boxes. This gives a high level view of the system.

## Heuristics on Design Practice
* **Iterative** - remember that [[Design|Design is an iterative process]]. 

* **Divide and conquer**. Divide the program into different areas of concern then tackle those areas individually

* Consider top down and bottom up approaches (see [[Design]])

* **Experimental [[details/creativity/design/DOET/Design Thinking|Prototyping]] - this relies on the following principles:
	* Write the absolute minimum of code needed to answer the question and no more.
	* Ask a specific design question
	* Remember that prototype code is throwaway code.

* **Consider Collaborative Design** Two heads are better than one.
	* A structured approach is better for quality assurance.
	* A less structured approach is better for creativity and design.

* **Determine how much design is enough** - when the design descends to the level of a task that you’ve done before or to a simple modification or extension of such a task, you’re probably ready to stop designing and begin coding.
	* While you can’t know the exact right amount of design with any confidence, *two amounts of design are guaranteed to be wrong every time: designing every last detail and not designing anything at all*

* **Capture Design Work** - the following are some alternatives to documentation
	* Insert design documentation into the code itself.
	* Use a Wiki 
	* Use summaries of the design discussion
	* Use pictures, diagrams or charts.
# Links
* [[Code Complete by McConnell]] - Ch. 5
* [[Design]]
* [[Clean Code Principles]]