# Planning
## Requirements 
### Specific Functional Requirements
* Are all the inputs to the system specified, including their source, accuracy, range of values, and frequency?
* Are all the outputs from the system specified, including their destination, accuracy, range of values, frequency, and format?
* Are all output formats specified for Web pages, reports, and so on?
* Are all the external hardware and software interfaces specified?
* Are all the external communication interfaces specified, including handshaking, error-checking, and communication protocols?
* Are all the tasks the user wants to perform specified?
* Is the data used in each task and the data resulting from each task specified?
### Specific Non-functional Requirements
* Is the expected response time, from the user’s point of view, specified for all necessary operations?
* Are other timing considerations specified, such as processing time, data transfer rate, and system throughput?
* Is the level of [[Cybersecurity|security]] specified?
* Is the reliability specified, including the consequences of software failure, the vital information that needs to be protected from failure, and the strategy for error detection and recovery?
* Are minimum machine memory and free disk space specified?
* Is the maintainability of the system specified, including its ability to adapt to changes in specific functionality, changes in the operating environment, and changes in its interfaces with other software?
* Is the definition of success included? Of failure?

### Requirements Quality
* Are the requirements written in the user’s language? Do the users think so?
* Does each requirement avoid conflicts with other requirements?
* Are acceptable tradeoffs between competing attributes specified—for example, between robustness and correctness?
* Do the requirements avoid specifying the deisgn?
* Are the requirements at a fairly consistent level of detail? Should any requirement be specified in more detail? Should any requirement be specified in less detail?
* Are the requirements clear enough to be turned over to an independent group for construction and still be understood? Do the developers think so?
* Is each item relevant to the problem and its solution? Can each item be traced to its origin in the problem environment?
* Is each requirement testable? Will it be possible for independent testing to determine whether each requirement has been satisfied?
* Are all possible changes to the requirements specified, including the likelihood of each change?

### Requirements Completeness
* Where information isn’t available before development begins, are the areas of incompleteness specified?
* Are the requirements complete in the sense that if the product satisfies every requirement, it will be acceptable?
* Are you comfortable with all the requirements? Have you eliminated requirements that are impossible to implement and included just to appease your customer or your boss?

## Architecture 
### Specific Topics
* Is the overall organization of the program clear, including a good architectural overview and justification?
* Are major building blocks well defined, including their areas of responsibility and their interfaces to other building blocks?
* Are all the functions listed in the requirements covered sensibly, by neither too many nor too few building blocks?
* Are the most critical classes described and justified?
* Is the data design described and justified?
* Is the [[Database]] organization and content specified?
* Are all key business rules identified and their impact on the system described?
* Is a strategy for the user interface design described?
* Is the user [[UX Design Principles|interface]] modularized so that changes in it won’t affect the rest of the program?
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

### General Quality
* Does the architecture account for all the requirements?
* Is any part overarchitected or underarchitected? Are expectations in this area set out explicitly?
* Does the whole architecture hang together conceptually?
* Is the top-level design independent of the machine and language that will be used to implement it?
* Are the motivations for all major decisions provided?
* Are you, as a programmer who will implement the system, comfortable with the architecture?

## Major Construction Practices
### Coding
* Have you defined how much design will be done up front and how much will be done at the keyboard, while the code is being written?
* Have you defined coding conventions for names, comments, and layout? 
* Have you defined specific coding practices that are implied by the architecture, such as how error conditions will be handled, how security will be addressed, what conventions will be used for class interfaces, what standards will apply to reused code, how much to consider performance while coding, and so on?
* Have you identified your location on the technology wave and adjusted your approach to match? If necessary, have you identified how you will program into the language rather than being limited by programming in it?
### Teamwork
* Have you defined an integration procedure—that is, have you defined the specific steps a programmer must go through before checking code into the master sources?
* Will programmers program in pairs, or individually, or some combination of the two?
### Quality Assurance
* Will programmers write test cases for their code before writing the code itself?
* Will programmers write unit tests for their code regardless of whether they write them first or last?
* Will programmers step through their code in the debugger before they check it in?
* Will programmers integration-test their code before they check it in? 
* Will programmers review or inspect each other’s code?
### Tools
* Have you selected a revision control tool?
* Have you selected a language and language version or compiler version?
* Have you selected a framework such as J2EE or Microsoft .NET or explicitly decided not to use a framework?
* Have you decided whether to allow use of nonstandard language features?
* Have you identified and acquired other tools you’ll be using—editor, refactoring tool, debugger, test framework, syntax checker, and so on?

# Design
## Class Design
### Abstract Data Types
* Have you thought of the classes in your program as abstract data types and evaluated their interfaces from that point of view?
### Abstraction
* Does the class have a central purpose?
* Is the class well named, and does its name describe its central purpose?
* Does the class’s interface present a consistent abstraction?
* Does the class’s interface make obvious how you should use the class?
* Is the class’s interface abstract enough that you don’t have to think about how its services are implemented? Can you treat the class as a black box?
* Are the class’s services complete enough that other classes don’t have to meddle with its internal data?
* Has unrelated information been moved out of the class?
* Have you thought about subdividing the class into component classes, and have you subdivided it as much as you can?
* Are you preserving the integrity of the class’s interface as you modify the class?

### Encapsulation
* Does the class minimize accessibility to its members?
* Does the class avoid exposing member data?
* Does the class hide its implementation details from other classes as much as the programming language permits?
* Does the class avoid making assumptions about its users, including its derived classes?
* Is the class independent of other classes? Is it loosely coupled?

### Inheritance
* Is inheritance used only to model “is a” relationships—that is, do derived classes adhere to the Liskov Substitution Principle?
* Does the class documentation describe the inheritance strategy?
* Do derived classes avoid “overriding” non-overridable routines?
* Are common interfaces, data, and behavior as high as possible in the inheritance tree?
* Are inheritance trees fairly shallow?
* Are all data members in the base class private rather than protected?

### Other Implementation Issues
* Does the class contain about seven data members or fewer?
* Does the class minimize direct and indirect routine calls to other classes?
* Does the class collaborate with other classes only to the extent absolutely necessary?
* Is all member data initialized in the constructor?
* Is the class designed to be used as deep copies rather than shallow copies unless there’s a measured reason to create shallow copies?

### Language Specific Issues
* Have you investigated the language-specific issues for classes in your specific programming language?

## Routine Design
### Big Picture Issues
* Is the reason for creating the routine sufficient?
* Have all parts of the routine that would benefit from being put into routines of their own been put into routines of their own?
* Is the routine’s name a strong, clear verb-plus-object name for a procedure or a description of the return value for a function?
* Does the routine’s name describe everything the routine does?
* Have you established naming conventions for common operations?
* Does the routine have strong, functional cohesion—doing one and only one thing and doing it well?
* Do the routines have loose coupling—are the routine’s connections to other routines small, intimate, visible, and flexible? Is the length of the routine determined naturally by its function and logic, rather than by an artificial coding standard?
### Parameter Passing Issues
* Does the routine’s parameter list, taken as a whole, present a consistent interface abstraction?
* Are the routine’s parameters in a sensible order, including matching the order of parameters in similar routines?
* Are interface assumptions documented?
* Does the routine have seven or fewer parameters?
* Is each input parameter used?
* Is each output parameter used?
* Does the routine avoid using input parameters as working variables?
* If the routine is a function, does it return a valid value under all possible circumstances?


## Defensive Programming
### General
* Does the routine protect itself from bad input data?
* Have you used assertions to document assumptions, including preconditions and postconditions?
* Have assertions been used only to document conditions that should never occur?
* Does the architecture or high-level design specify a specific set of error handling techniques?
* Does the architecture or high-level design specify whether error handling should favor robustness or correctness?
* Have barricades been created to contain the damaging effect of errors and reduce the amount of code that has to be concerned about error processing?
* Have debugging aids been used in the code?
* Have debugging aids been installed in such a way that they can be activated or deactivated without a great deal of fuss?
* Is the amount of [[Defensive Programming]] code appropriate—neither too much nor too little?
* Have you used offensive-programming techniques to make errors difficult to overlook during development?
## Exceptions
* Has your project defined a standardized approach to exception handling?
* Have you considered alternatives to using an exception?
* Is the error handled locally rather than throwing a nonlocal exception, if possible?
* Does the code avoid throwing exceptions in constructors and destructors?
* Are all exceptions at the appropriate levels of abstraction for the routines that throw them?
* Does each exception include all relevant exception background information?
* Is the code free of empty catch blocks? (Or if an empty catch block truly is appropriate, is it documented?)
## Security 
* Does the code that checks for bad input data check for attempted buffer overflows, SQL injection, HTML injection, integer overflows, and other malicious inputs?
* Are all error-return codes checked?
* Are all exceptions caught?
* Do error messages avoid providing information that would help an attacker break into the system?

# Links
* [[Code Complete by McConnell]] - primary source
* [[Software Construction]]

* [[Object Oriented Programming]]
* [[SOLID Design Principles]]
* [[Cohesion and Coupling]]