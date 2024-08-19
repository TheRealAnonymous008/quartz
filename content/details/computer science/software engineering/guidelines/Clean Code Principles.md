# General Principles
* Be Consistent
* Be Precise
* To maintain code easier, ensure it is clean at every step of the development process
* We aren't done when the program works. We still have to maintain and clean the code.
* Don't Repeat Yourself
* **Law of Demeter**:  A module should now know the innards of the objects it manipulates.
  A method $f$ of a class $C$ should only call the methods of these 
	* *$C$
	* An object created by $f$
	* An object passed as an argument to $f$
	* An object held in an instance variable of $C$.
     
    $f$ should not invoke methods on objects that are returned by any of the allowed functions
* **Principle of Least Surprise**:  Do not include unexpected behaviors.
* Don't ignore the compiler's warnings. They are trying to tell you something.
* Learn and understand the algorithms you are employing.
* **[[SOLID Design Principles|SOLID]] Principles** make code more flexible and maintainable.
* Use a version control system (i.e. [[Git]]).
# Naming
* Use names which reveal intent. Names shouldn’t require comments to explain them.
* Avoid names which assume implicit knowledge of context. Don’t use colloquialisms or slang.
* Avoid using words whose entrenched meanings vary from the intended meaning. Avoid using confusing words.
* Use names which can distinguish the object it describes from other objects. Avoid number-series naming (`a1`, `a2`, …) and using noise words like _info_ and _data_
* Use names which can be pronounced.
* Use names which can be easily searched through the IDE’s search tools.
* The length of a name should correspond to the size of its scope.
* Avoid encodings such as the Hungarian notation.
* Use names which are clear in the context of the priblem and solution to avoid having to mentally map names.
* Classes should be named with nouns and noun phrases.
* Methods and subroutines should be named with verbs and verb phrases. Use names which describe what the function does.
* Accessors, mutators and predicates should be named for their value and prefixed with `get`, `set`, and `is`.
* Be consistent in the choice of words per concept. One word per concept.
* Don’t use the same name for two purposes. 
* If all else fails, ensure the name has meaningful context.
* Add no more context to a name than is necessary.
* Name all your constants instead of using “magic numbers”
# Functions
* Functions should be as small as possible.
* Functions should not be large enough to hold deeply nested structures.
* Functions should do one thing. They should do it well. They should do it only.
* Statements in the function should be on the same level of abstraction
* Steps within the function should describe the steps to perform what the function is intended to do.
* Exploit polymorphism and inheritance to ensure switch statements are never repeated and that code is easier to maintain.
* The fewer the arguments the better.
* Avoid passing Booleans as arguments. This violates the do-one-thing principle.
* Ensure the order which arguments are passed (if order is important) is clear from the name of the function.
* Ensure functions do what they are intended to do and nothing else. They should have no side effects.
* Avoid arguments which are outputs of the function. If the state of something must be changed, have the function change the state of that thing’s owning object.
* **Command Query Separation**: Functions either do something or return something but never both.
* Discard functions which are never going to be called.
* Make temporal [[Cohesion and Coupling|couplings]] explicit.
# Conditionals
* Favor polymorphism over if/else and switch statements.
* Avoid using negative conditionals.
* Encapsulate your conditionals in a separate function.
# Comments
* *Don’t use comments to compensate for bad code.*
* *If comments can be removed, remove them.*
* Good comments:
	* Legal comments
	* Informative comments
	* Explanation of intent
	* Clarification.
	* Warning of consequences.
	* TO-DO comments
	* Amplification of importance.
* Bad comments
	* Comments which are left for no apparent reason.
	* Redundant comments
	* Misleading comments
	* Mandated comments
	* Journal comments added at the start at every edit.
	* Comments which provide no information.
	* Inaccurate comments / Obsolete comments
	* Position markers.
	* Comments which can be explained by the function / variable’s name.
	* Attributions and Bylines
	* Commented out code (unless it’s there for a reason).
	* [[HTML]] comments
	* Comments that describe nonlocal information
	* Comments that describe too much information
	* Comments which don’t obviously describe the code.
# Formatting
* Small files are easier to understand than larger files.
* **The Newspaper Rule**: Files should be organized. Lower level code at the bottom, higher level functionality at the top.
* Separate concepts / groups of code with vertical spacing (i.e. line breaks).
* Concepts that are closely related should be vertically closer together.
* Unless you have a good reason to, avoid separating related concepts in separate files.
* Declare function variables close to where they are used.
* Be consistent on where variables are declared.
* Functions which call other functions should be closer, and callers should be above their callees if possible.
* Functions which perform similar operations should be closer together.
* Shorter lines are better.
* Use horizontal white space to accentuate operations which are unrelated.
* Use indentations to accentuate hierarchy within the code.
* Blocks which only contain one line should still be indented to make things readable.
* Separate code on different levels of abstraction.
# Objects and Data Structures
* Principle of **encapsulation**: Keep variables private to minimize dependencies.
* Hiding implementation is about  **abstraction**: expose abstract interfaces that allow clients to manipulate the data without knowing the implementation.
* Objects hide data and expose behaviors. Data structures expose data and have no behaviors.
* Procedural code (using data structures) makes it easy to add new functions without changing the existing data structures.
* [[Object Oriented Programming|Object Oriented]] Code code makes it easy to add new classes without changing existing functions.
* Not everything should be an object.
* Avoid chains of calls. Split function calls apart.
* Avoid creating hybrids of data structures and objects. Creating an object means we want its functions to do something. Creating a [[Data Structures|Data structure]] / procedural code means we want to ask about its internals.
# Error Handling
* Avoid obscuring code logic with error handling.\
* Prefer exceptions to returning error codes. Error codes are confusing, lead to dependencies, and violate Command Query Separation
* Error handling is one thing. Try-catch blocks should be their own functions and not included in a function itself.
* When writing code that can throw errors, write the try-catch-finally blocks first. This makes code invariants clear.
* Provide context with exceptions to locate errors in the code: Create informative error messages.
* Define exception classes based on the caller’s needs. In these classes, determine how the error was caught.
* Use decorators to wrap third party APIs into calls
* Use the **Special Case Pattern**—a class specifically designed to handle unique special cases by encapsulating the special behavior.
* Don’t return null pointers. Minimize the amount of NullPointerExceptions checked. Use try-catch or the Special Case pattern instead.
* Avoid passing in the null pointer as much as possible.
* By default, forbid the passing of null to functions and methods.
# Boundaries and Third Party Software
* In general, providers aim to give general functionality while users only use parts of the code that are needed.
* Avoid passing or returning boundary interfaces. Instead, encapsulate these inside a class. **Boundary interfaces** refer to interfaces to be used by another program and ones which can potentially change.
* Write tests for third-party code to be used.
* Write tests to explore understanding of third-party code.
* Encapsulate code from third-party software into your own classes. This is so code can vary independent of the class or third-party software
* Use learning tests to understand changes to third party software
* Use the adapter pattern along with custom user interfaces to utilize code that is still in production.
* Make logical dependencies physical: explicitly ask modules for dependencies.
# Unit Testing and TDD
* Write tests to make sure every part of the code works as intended. Tests and Production code must be written together.
* Do not write production code unless you have written a failing unit test.
* Do not write more of a test code than is sufficient to fail and not compiling is failing.
* Do not write more production code than is sufficient to pass the currently failing test.
* Test code must keep up with Production code; ergo, keep test code clean.
* Use the **Build Operate Check** Pattern: Build Test Data, Operate on the Test Data and Check if it is correct.
* It’s okay to be inefficient in tests
* Use the **Give-When-Then** to make tests easier to read: Build corresponds to Give, When to Operate, and Then to Check.
* Use the Template Method pattern to define a template method for give and when.
* Minimize the number of asserts in the unit test.
* Test only one thing per test function
* Follow the rule of **FIRST**. Tests should be:
	* Fast
	* Independent of each other
	* Repeatable in any environment
	* Self-validating (has Boolean values to determine pass or fail)
	* Timely: Written before production code.
* Test for boundary and corner cases.
* Don’t skip trivial tests.
* Exhaustively test near functions where bugs were found.
* Patterns of failure are revealing.
* Test coverage patterns can be revealing. Look at code which is or is not executed.
# Classes
* Classes should begin with a list of variables: Public static constants first, followed by private static variables, followed by private instance variables.
* Keep variables and utility functions private as much as possible. Only use protected and package as a last resort, and almost always never use public variables.
* Keep classes small. less responsbility the better.
* The  name of a class should describe what responsibilities it fulfills. Remember the Single Responsibility Principle.
* Keep the number of instance variables small.
* Keep classes as cohesive as possible: Methods should manipulate as much of the variables as possible. Keep methods and members co-dependent on each other.
* When classes lose cohesion, split them.
* When there are many instance variables in methods, it is usually a sign that classes need to be separated so these instance variables can be removed.
* Structure the class so you have to change as little code as possible. Remember the open-closed principle
* Minimize dependencies to concrete details to make testing the class easier. Remember the dependency inversion principle.
* Base classes should not depend on their derivatives.
* Don’t introduce artificial coupling. If objects shouldn’t depend on each other, then they shouldn’t be coupled.
* Favor non-static methods unless you are absolutely sure that your methods will not change polymorphically
# Systems
* Separate constructing a system from using it.
* Modularize the process of constructing and initializing an object to minimize dependencies.
	* Have the main function be the one to build the system and pass all needed objects to the application. This has the benefit of the application having no knowledge of main or the construction, only that everything is built properly.
	* Use an abstract factory / factory methods to separate details of implementation with abstraction. This allows the application to be in control of how objects are built.
	* Use dependency injection – objects receive the other objects it depends on. Instead of objects taking responsibility for its own dependencies, it should instead pass this responsibility to another authoritative mechanism.
* Allow for the system to incrementally grow by following the SOLID principles and minimize coupling.
* Conside **concerns**—aspects which can affect the code of the program. In particular, apart from the core concern (why the program was built), there are **cross cutting concerns** which end up affecting multiple parts of the code. It is important to make the code flexible and extensible
* A good API should largely disappear from view most of the time.
* Different extensions of the application should be possible through minimally invasive aspects or other Aspect-like tools.
* Use standards when they add demonstrable value. Be warned that some standards hinder with the ability of the program to serve its purpose.
* Use a domain specific language to minimize a domain concept with the code that implements it.
# Emergent Designs
* Keep designs simple
* A design is simple if it follows these rules, in decreasing order of priority. (Kent Beck)
	* Runs all the tests
	* Contains no duplication
	* Expresses the intent of the programmer.
	* Minimizes the number of classes and methods
# Concurrency
* Use [[Multiprogramming|Concurrency]] to decouple what gets done from when it gets done.
* General guidelines about Concurrency to consider:
	* Concurrency can sometimes improve performance, but only when there is a lot (non-trivial amount) of wait time that can be shared between multiple threads or processors
	* Changing to a multi-threaded design demands a change in design.
	* Understanding concurrency issues remain important.
	* Concurrency incurs some overhead, both in performance, as well as additional code.
	* Correct concurrency is complex even for simple problems.
	* Concurrency bugs aren’t usually repeatable, so they are often ignored as one-offs instead of the true defects that they are
	* Concurrency demands a fundamental change in design strategy.
 * Concurrency defense principles:
	* Use the Single Responsibility Principle.. Separate concurrent code from other code
		* Concurrency related code has its own life cycle of development, change and tuning.     
		* Concurrency related code has its own challenges separate from non-concurrent code.
	* Use encapsulation: limit the access of any data that may be shared.
		* It helps prevent code from breaking when it modifies shared data.
		* It prevents duplication of effort required to make everything is thread-safe.
		* It lessens the burden on finding failures.
	* Use copies of data instead of the actual data.
	* Parition data into independent subsets that can be operated on by independent threads, possibly in different processors.
* Know the library you are working with.
	* Use the provided thread-safe collections
	* Use the executor framework for executing unrelated tasks.
	* Use nonblocking solutions when possible.
	* Note library classes which are not thread safe.
* Avoid using more than one method  on a shared object. Beware dependencies between synchronized models.
* When more than one method must be used on a shared object, use the following:
	* **Client Based Locing** - client locks the server before calling the first method. The lock's extent includes the code calling the last method.
	* **Server Based Locking** - locking occurs within. The server creates a subroutine that locks the server, calls all the methods and then unlocks. Clients call this method.
	* **Adapted Server** - create an intermediary method that performs the locking
* Keep synchronized sections as small as possible.
* Think about shut-down code early and getting it working early.
* Write tests that have the potential to expose problems, and then run them frequently with different programmatic configurations and system configurations and load.
	* Treat spurious failures as candidate threading issues: Do not ignore system failures as one-offs.
	* Get non-threading code to work first.
	* Make thread code pluggable so it runs in various configurations such as:
		* One thread, several threads, varied as it executes.
		* Threaded code interacts with something that can be both real or a test double.
		* Execute with test doubles that run quickly, slowly, variable.
		* Configure tests so they can run for a number of iterations.
* Make thread code tunable. Allow for changes brought about by the system.
* Run with more threads than processors to promote task swapping and catch deadlocks.
* Run on different platforms early and often.
* Instrument your code to try and force failures. Make it run code that forces it to execute threads in different orderings.
# Links
* [[Clean Code by Robert Martin]]
* [[Object Oriented Programming]]
* [[Programming]]

* [Why You Shouldn't Nest Your Code by CodeAesthetic](https://www.youtube.com/watch?v=CFRhGnuXG-4) - There are two ways to reduce nesting in code
	* Extract bits of code and refactor them to their own functions
	* Invert breaking conditions and have them break early.