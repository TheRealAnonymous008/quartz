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
* **Problem Definition Prerequisite** - a clear statement of the problem that the system is supposed to solve.
	* The problem statement should not reference any solution.
	* The problem statement should be described from a user's point of view (unless the problem is of a technical nature)
	* *Defining the wrong problem means wasting time solving the wrong problem*

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

## Requirements Checklist
* **Specific Functional Requirements**
	* Are all the inputs to the system specified, including their source, accuracy, range of values, and frequency?
	* Are all the outputs from the system specified, including their destination, accuracy, range of values, frequency, and format?
	* Are all output formats specified for Web pages, reports, and so on?
	* Are all the external hardware and software interfaces specified?
	* Are all the external communication interfaces specified, including handshaking, error-checking, and communication protocols?
	* Are all the tasks the user wants to perform specified?
	* Is the data used in each task and the data resulting from each task specified?
* **Specific Non-functional Requirements**
	* Is the expected response time, from the user’s point of view, specified for all necessary operations?
	* Are other timing considerations specified, such as processing time, data transfer rate, and system throughput?
	* Is the level of [[Cybersecurity|security]] specified?
	* Is the reliability specified, including the consequences of software failure, the vital information that needs to be protected from failure, and the strategy for error detection and recovery?
	* Are minimum machine memory and free disk space specified?
	* Is the maintainability of the system specified, including its ability to adapt to changes in specific functionality, changes in the operating environment, and changes in its interfaces with other software?
	* Is the definition of success included? Of failure?
* **Requirements Quality**
	* Are the requirements written in the user’s language? Do the users think so?
	* Does each requirement avoid conflicts with other requirements?
	* Are acceptable tradeoffs between competing attributes specified—for example, between robustness and correctness?
	* Do the requirements avoid specifying the [[Design]]?
	* Are the requirements at a fairly consistent level of detail? Should any requirement be specified in more detail? Should any requirement be specified in less detail?
	* Are the requirements clear enough to be turned over to an independent group for construction and still be understood? Do the developers think so?
	* Is each item relevant to the problem and its solution? Can each item be traced to its origin in the problem environment?
	* Is each requirement testable? Will it be possible for independent testing to determine whether each requirement has been satisfied?
	* Are all possible changes to the requirements specified, including the likelihood of each change?
* **Requirements Completeness**
	* Where information isn’t available before development begins, are the areas of incompleteness specified?
	* Are the requirements complete in the sense that if the product satisfies every requirement, it will be acceptable?
	* Are you comfortable with all the requirements? Have you eliminated requirements that are impossible to implement and included just to appease your customer or your boss?

## Architecture Checklist
* **Specific Topics**
	* Is the overall organization of the program clear, including a good architectural overview and justification?
	* Are major building blocks well defined, including their areas of responsibility and their interfaces to other building blocks?
	* Are all the functions listed in the requirements covered sensibly, by neither too many nor too few building blocks?
	* Are the most critical classes described and justified?
	* Is the data design described and justified?
	* Is the database organization and content specified?
	* Are all key business rules identified and their impact on the system described?
	* Is a strategy for the user interface design described?
	* Is the user interface modularized so that changes in it won’t affect the rest of the program?
	* Is a strategy for handling I/O described and justified?
	* Are resource-use estimates and a strategy for resource management described and justified for scarce resources like threads, database connections, handles, network bandwidth, and so on?
	* Are the architecture’s security requirements described?
	* Does the architecture set space and speed budgets for each class, subsystem, or functionality area?
	* Does the architecture describe how scalability will be achieved?
	* Does the architecture address interoperability?
	* Is a strategy for internationalization/localization described?
	* Is a coherent error-handling strategy provided?
	* Is the approach to fault tolerance defined (if any is needed)?
	* Has technical feasibility of all parts of the system been established?
	* Is an approach to overengineering specified?
	* Are necessary buy-vs.-build decisions included?
	* Does the architecture describe how reused code will be made to conform to other architectural objectives?
	* Is the architecture designed to accommodate likely changes?

* **General Quality**
	* Does the architecture account for all the requirements?
	* Is any part overarchitected or underarchitected? Are expectations in this area set out explicitly?
	* Does the whole architecture hang together conceptually?
	* Is the top-level design independent of the machine and language that will be used to implement it?
	* Are the motivations for all major decisions provided?
	* Are you, as a programmer who will implement the system, comfortable with the architecture?

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
## Major Construction Practices Checklist
* **Coding** 
	* Have you defined how much design will be done up front and how much will be done at the keyboard, while the code is being written?
	* Have you defined coding conventions for names, comments, and layout? 
	* Have you defined specific coding practices that are implied by the architecture, such as how error conditions will be handled, how security will be addressed, what conventions will be used for class interfaces, what standards will apply to reused code, how much to consider performance while coding, and so on?
	* Have you identified your location on the technology wave and adjusted your approach to match? If necessary, have you identified how you will program into the language rather than being limited by programming in it?
* **Teamwork**
	* Have you defined an integration procedure—that is, have you defined the specific steps a programmer must go through before checking code into the master sources?
	* Will programmers program in pairs, or individually, or some combination of the two?
* **Quality Assurance**
	* Will programmers write test cases for their code before writing the code itself?
	* Will programmers write unit tests for their code regardless of whether they write them first or last?
	* Will programmers step through their code in the debugger before they check it in?
	* Will programmers integration-test their code before they check it in? 
	* Will programmers review or inspect each other’s code?
* **Tools**
	* Have you selected a revision control tool?
	* Have you selected a language and language version or compiler version?
	* Have you selected a framework such as J2EE or Microsoft .NET or explicitly decided not to use a framework?
	* Have you decided whether to allow use of nonstandard language features?
	* Have you identified and acquired other tools you’ll be using—editor, refactoring tool, debugger, test framework, syntax checker, and so on?
# Links
* [[Code Complete by McConnell]] - Ch. 3, 4
	* Ch. 3 - Requirements Checklist
	* Ch. 3 - Architecture Checklist
	* Ch. 4 - Major Construction Practices Checklist