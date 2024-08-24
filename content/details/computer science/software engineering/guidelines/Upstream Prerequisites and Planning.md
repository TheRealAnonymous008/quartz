* The process of [[Software Construction]] requires planning and preparation. 

# Rules of Thumb
* *Measure twice; Cut once* especially when constructing large, complex software
* *Detect defects as early as possible*. This reduces defect correction costs. 
* *Pareto principle applies*: There are two approachehs:
	* Specify 80% of the requirements up front, allocate time for additional requirements, and then practice systematic change control to accept only the most valuable new requirements as the project progresses
	* Specify the most important 20% of the requirements up front and develop the rest in small increments.
* *Choose between Iterative and Sequential approaches with the following in mind*

| Iterative                                                 | Sequential                                          |
| --------------------------------------------------------- | --------------------------------------------------- |
| Requirements are not well understood or unstable          | Stable requirements                                 |
| Complex design                                            | Straightforward and well-understood design          |
| Development team is unfamiliar with the applications area | Development team is familiar with the domain        |
| High-risk project                                         | Low-risk project                                    |
| Long-term predictability is not important                 | Long-term predictability is important               |
| The cost of downstream changes is likely to be low        | The cost of downstream changes is likely to be high |

* Iterative approaches tend to be preferred since the typical project is complex. However, note *Iterative approaches tend to reduce the impact of inadequate upstream work, but they don’t eliminate it*
* Spend about 10-20% of the effort and 20-30% of the schedule to requirements, architecture, and up-front planning. However, bottom line: *Allow time for defining the requirements*. For volatile requirements, *the requirements can sometimes be their own project*
* *Always rationalize design decisions*. Preferably, present alternatives and explain why they were not considered.
	* During construction, this gives insight into the design decisions of the architect. 
	* Present the objectives of the architecture.
* *A good architecture should fit the problem*. When you look at the architecture, you should be pleased by how [[The Timeless Way of Building|natural]] and easy the solution seems.
	* Good software architecture is largely machine- and language-independent
	* The architecture should tread the line between underspecifying and overspecifying the system
# Rationale
* The overarching goal of preparation is risk reduction: a good project planner clears major risks out of the way as early as possible so that the bulk of the project can proceed as smoothly as possible
* *The importance of upstream planning is as follows*
	* Planning means *understanding what you want to build* so that you don’t waste money building the wrong thing.
	* If you are planning a highly iterative project, you will need to *identify the critical requirements and architectural elements* that apply to each piece you’re constructing before you begin construction.
	* It pays to do things right the first time. *Unnecessary changes are expensive*. Since requirements are done first, requirements defects have the potential to be in the system longer and to be more expensive.
# Prerequisites
* **Problem Definition Prerequisite** - a [[Ideation|clear statement of the problem]] that the system is supposed to solve.
	* The problem statement should not reference any solution.
	* The problem statement should be described from a user's point of view (unless the problem is of a technical nature)
	* *[[Conceptual Blocks to Ideation|Defining the wront problem]] means wasting time solving the wrong problem*

* **Requirements Prerequisite** - a statement of what the software system is supposed to do.
	* Explicit requirements help to ensure that the user rather than the programmer drives the system’s functionality. We don't have to guess what the user wants.
	* Explicit requirements is the ground source of truth regarding what the program is supposed to do.
	* Having explicit requirements minimizes the number of changes to the system (and therefore the cost of changing them)
	* *The development process helps customers better understand their own needs, and this is a major source of requirements changes* . Here are some ways to handle requirements changes
		* Assess the quality of your requirements (see [[#Requirements Checklist]])
		* Make sure everyone knows the cost of requirements changes (esp. the client)
		* Establish a formal change-control procedure so that the customer does not frequently change the requirements (as a bonus, the customer is assured that their input is considered)
		* Use short development cycles to respond to your users quickly.
		* Dump the project if requirements are too volatile.
		* Evaluate the added business value of each requirement.
	* *Defining the wrong requirements means that you might've missed important details of the problem* .

* **Architecture Prerequisite** - a document detailing the design constraints that apply system-wide or at the subsystem level.
	* The quality of the architecture determines the conceptual integrity of the system.
	* Architectural changes are expensive to make during construction or later.
	* *Defining the wrong architectural design might mean you are solving the problem the wrong way*

## Architecture Considerations
* **Program Organization** - an overview describing the [[System Science|system]] in broad terms.
	* The architecture should define the major building blocks in a program. Each building block should have a specific [[SOLID Design Principles|responsibility]].  
	* The communication rules for each building block should be well defined
* **Major Classes** - the architecture specifies the major classes and how each class interacts with each other. 
* **Data Design** - describe the major files and table designs to be used.  The architecture should specify the high-level organization and contents of any [[Database|databases]] used.
* **Business Rules** - describe the business rules the architecture depends on. 
* **User Interface Design** - the [[UX Design Principles|UX]] and UI is specified either in the requirements phase or architecture phase 
	* Separate UI from the rest of the code to allow substitution with other UI layouts.
* **Resource Management** - The architecture should describe a plan for managing scarce resources such as database connections, [[Multiprogramming|threads]],  [[Computer Organization|memory]], and handles. This includes estimates for typical usage. 
* **Security** - the architecture describes its approach to [[Cybersecurity|security]]. 
* **Performance** - performance goals should be specified if it is a concern. Include performance estimates .
* **Scalability** - can the system grow and if so, how? If not, specify that the system will not grow
* **Interoperability** - the architecture should describe how the system will share data with other software or hardware.
* **Localization** - especially for interactive systems, will the system support different locales?
* **Input/Output** - the architecture should specify the level at which I/O errors are detected.
* **Error Processing** - specify a strategy for error handling in the architecture. 
	* Is the error processing *corrective* (it recovers from the errors) or *detective* (will the program continue as if nothing happened or quit)
	* Is it *active* (it anticipates errors) or *passive* (it responds only when it can't avoid them)? 
	* How do error  propagate. 
	* What are the conventions for handling error messages.
	* How will exceptions be handled? Where can exceptions be thrown and how will they be caught, logged and documented.
	* At what level are errors handled?
	* What is the level of responsibility of each class for validating its input data? 
	* Do you build your own exception-handling mechanism.
* **Fault Tolerance** - indicate the level of fault tolerance -- the ability to detect errors, recover from them if possible, and containing their effects if not
* **Architectural Feasibility** - can the architecture support the designed system? Can the architecture's limitations be mitigated?
* **Overengineering** - should programmers overengineer or do the simplest thing that works? This makes the system uniformly robust.
* **Buy vs Build** - can some components be bought from other sources? Why or why not? 
* **Reuse Decisions** - can reused software be made to conform to the other architectural goals if at all.
* **Change Strategy** - how will the architecture handle changes? 


## Construction Decisions
* Consider the [[Programming|programming language]] to be used.
	* Programmers are more productive using a familiar language than an unfamiliar one
	* Programmers working with high-level languages achieve better productivity and quality than those working with lower-level languages
* Consider programming conventions
	* It reduces cognitive load when reading and writing the code.
* Consider your location in the technology wave.
	* If you’re in the late part of the wave, you can plan to spend most of your day steadily writing new functionality. 
	* If you’re in the early part of the wave, you can assume that you’ll spend a sizeable portion of your time trying to figure out your programming language
	* *Your programming tools don’t have to determine how you think about programming*. Programming conventions should be language independent.
# Links
* [[Code Complete by McConnell]] - Ch. 3, 4
	* Ch. 3 - Requirements Checklist
	* Ch. 3 - Architecture Checklist
	* Ch. 4 - Major Construction Practices Checklist