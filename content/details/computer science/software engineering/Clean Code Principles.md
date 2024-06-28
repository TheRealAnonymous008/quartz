# General Principles
1. Be Consistent
2. Be Precise
3. To maintain code easier, ensure it is clean at every step of the development process
4. We aren't done when the program works. We still have to maintain and clean the code.
5. Don't Repeat Yourself
6. **Law of Demeter**:  A module should now know the innards of the objects it manipulates.
   A method $f$ of a class $C$ should only call the methods of these 
   * *$C$
   * An object created by $f$
   * An object passed as an argument to $f$
   * An object held in an instance variable of $C$.
     
    $f$ should not invoke methods on objects that are returned by any of the allowed functions
7. **Principle of Least Surprise**:  Do not include unexpected behaviors.
8. Don't ignore the compiler's warnings. They are trying to tell you something.
9. Learn and understand the algorithms you are employing.
10. **SOLID Principles** make code more flexible and maintainable.
11. Use a version control system (i.e. [[Git]]).
# Naming
1. Use names which reveal intent. Names shouldn’t require comments to explain them.
2. Avoid names which assume implicit knowledge of context. Don’t use colloquialisms or slang.
3. Avoid using words whose entrenched meanings vary from the intended meaning. Avoid using confusing words.
4. Use names which can distinguish the object it describes from other objects. Avoid number-series naming (`a1`, `a2`, …) and using noise words like _info_ and _data_
5. Use names which can be pronounced.
6. Use names which can be easily searched through the IDE’s search tools.
7. The length of a name should correspond to the size of its scope.
8. Avoid encodings such as the Hungarian notation.
9. Use names which are clear in the context of the priblem and solution to avoid having to mentally map names.
10. Classes should be named with nouns and noun phrases.
11. Methods and subroutines should be named with verbs and verb phrases. Use names which describe what the function does.
12.  Accessors, mutators and predicates should be named for their value and prefixed with `get`, `set`, and `is`.
13.  Be consistent in the choice of words per concept. One word per concept.
14.  Don’t use the same name for two purposes. 
15.  If all else fails, ensure the name has meaningful context.
16.  Add no more context to a name than is necessary.
17.  Name all your constants instead of using “magic numbers”
# Functions
1.     Functions should be as small as possible.
2.     Functions should not be large enough to hold deeply nested structures.
3.     Functions should do one thing. They should do it well. They should do it only.
4.     Statements in the function should be on the same level of abstraction
5.     Steps within the function should describe the steps to perform what the function is intended to do.
6.     Exploit polymorphism and inheritance to ensure switch statements are never repeated and that code is easier to maintain.
7.     The fewer the arguments the better.
8.     Avoid passing booleans as arguments. This violates the do-one-thing principle.
9.     Ensure the order which arguments are passed (if order is important) is clear from the name of the function.
10.  Ensure functions do what they are intended to do and nothing else. They should have no side effects.
11.  Avoid arguments which are outputs of the function. If the state of something must be changed, have the function change the state of that thing’s owning object.
12.  **Command Query Separation**: Functions either do something or return something but never both.
13.  Discard functions which are never going to be called.
14.  Make temporal couplings explicit.
# Conditionals
1. Favor polymorphism over if/else and switch statements.
2. Avoid using negative conditionals.
3. Encapsulate your conditionals in a separate function.
# Comments
1. Don’t use comments to compensate for bad code.
2. If comments can be removed, remove them.
3. Good comments:
	* Legal comments
	* Informative comments
	* Explanation of intent
	* Clarification.
	* Warning of consequences.
	* TO-DO comments
	* Amplification of importance.
4. Bad comments
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
	* HTML comments
	* Comments that describe nonlocal information
	* Comments that describe too much information
	* Comments which don’t obviously describe the code.
# Formatting
1. Small files are easier to understand than larger files.
2. **The Newspaper Rule**: Files should be organized. Lower level code at the bottom, higher level functionality at the top.
3. Separate concepts / groups of code with vertical spacing (i.e. line breaks).
4. Concepts that are closely related should be vertically closer together.
5. Unless you have a good reason to, avoid separating related concepts in separate files.
6. Declare function variables close to where they are used.
7. Be consistent on where variables are declared.
8. Functions which call other functions should be closer, and callers should be above their callees if possible.
9. Functions which perform similar operations should be closer together.
10. Shorter lines are better.
11. Use horizontal white space to accentuate operations which are unrelated.
12. Use indentations to accentuate hierarchy within the code.
13. Blocks which only contain one line should still be indented to make things readable.
14. Separate code on different levels of abstraction.
# Objects and Data Structures
1. Principle of **encapsulation**: Keep variables private to minimize dependencies.
2. Hiding implementation is about  **abstraction**: expose abstract interfaces that allow clients to manipulate the data without knowing the implementation.
3. Objects hide data and expose behaviors. Data structures expose data and have no behaviors.
4. Procedural code (using data structures) makes it easy to add new functions without changing the existing data structures.
5. [[Object Oriented Programming|Object Oriented]] Code code makes it easy to add new classes without changing existing functions.
6. Not everything should be an object.
7. Avoid chains of calls. Split function calls apart.
8. Avoid creating hybrids of data structures and objects. Creating an object means we want its functions to do something. Creating a [[Data Structures|Data structure]] / procedural code means we want to ask about its internals.
# Error Handling
1. Avoid obscuring code logic with error handling.
2. Prefer exceptions to returning error codes. Error codes are confusing, lead to dependencies, and violate Command Query Separation
3. Error handling is one thing. Try-catch blocks should be their own functions and not included in a function itself.
4. When writing code that can throw errors, write the try-catch-finally blocks first. This makes code invariants clear.
5. Provide context with exceptions to locate errors in the code: Create informative error messages.
6. Define exception classes based on the caller’s needs. In these classes, determine how the error was caught.
7. Use decorators to wrap third party APIs into calls
8. Use the **Special Case Pattern**—a class specifically designed to handle unique special cases by encapsulating the special behavior.
9. Don’t return null pointers. Minimize the amount of NullPointerExceptions checked. Use try-catch or the Special Case pattern instead.
10. Avoid passing in the null pointer as much as possible.
11. By default, forbid the passing of null to functions and methods.
# Boundaries and Third Party Software
1. In general, providers aim to give general functionality while users only use parts of the code that are needed.
2. Avoid passing or returning boundary interfaces. Instead, encapsulate these inside a class. Boundary interfaces refer to interfaces to be used by another program and ones which can potentially change.
3. Write tests for third-party code to be used.
4. Write tests to explore understanding of third-party code.
5. Encapsulate code from third-party software into your own classes. This is so code can vary independent of the class or third-party software
6. Use learning tests to understand changes to third party software
7. Use the adapter pattern along with custom user interfaces to utilize code that is still in production.
8. Make logical dependencies physical: explicitly ask modules for dependencies.
# Unit Testing and TDD
1. Write tests to make sure every part of the code works as intended. Tests and Production code must be written together.
2. Do not write production code unless you have written a failing unit test.
3. Do not write more of a test code than is sufficient to fail and not compiling is failing.
4. Do not write more production code than is sufficient to pass the currently failing test.
5. Test code must keep up with Production code; ergo, keep test code clean.
6. Use the **Build Operate Check** Pattern: Build Test Data, Operate on the Test Data and Check if it is correct.
7. It’s okay to be inefficient in tests
8. Use the **Give-When-Then** to make tests easier to read: Build corresponds to Give, When to Operate, and Then to Check.
9. Use the Template Method pattern to define a template method for give and when.
10. Minimize the number of asserts in the unit test.
11. Test only one thing per test function
12.  Follow the rule of **FIRST**. Tests should be:
	* Fast
	* Independent of each other
	* Repeatable in any environment
	* Self-validating (has Boolean values to determine pass or fail)
	* Timely: Written before production code.
13. Test for boundary and corner cases.
14. Don’t skip trivial tests.
15. Exhaustively test near functions where bugs were found.
16. Patterns of failure are revealing.
17. Test coverage patterns can be revealing. Look at code which is or is not executed.
# Classes
1. Classes should begin with a list of variables: Public static constants first, followed by private static variables, followed by private instance variables.
2. Keep variables and utility functions private as much as possible. Only use protected and package as a last resort, and almost always never use public variables.
3. Keep classes small. less responsbility the better.
4. The  name of a class should describe what responsibilities it fulfills. Remember the Single Responsibility Principle.
5. Keep the number of instance variables small.
6. Keep classes as cohesive as possible: Methods should manipulate as much of the variables as possible. Keep methods and members co-dependent on each other.
7. When classes lose cohesion, split them.
8. When there are many instance variables in methods, it is usually a sign that classes need to be separated so these instance variables can be removed.
9. Structure the class so you have to change as little code as possible. Remember the open-closed principle
10. Minimize dependencies to concrete details to make testing the class easier. Remember the dependency inversion principle.
11. Base classes should not depend on their derivatives.
12. Don’t introduce artificial coupling. If objects shouldn’t depend on each other, then they shouldn’t be coupled.
13. Favor non-static methods unless you are absolutely sure that your methods will not change polymorphically
# Systems
1. Separate constructing a system from using it.
2. Modularize the process of constructing and initializing an object to minimize dependencies.
	* Have the main function be the one to build the system and pass all needed objects to the application. This has the benefit of the application having no knowledge of main or the construction, only that everything is built properly.
	* Use an abstract factory / factory methods to separate details of implementation with abstraction. This allows the application to be in control of how objects are built.
	* Use dependency injection – objects receive the other objects it depends on. Instead of objects taking responsibility for its own dependencies, it should instead pass this responsibility to another authoritative mechanism.
3. Allow for the system to incrementally grow by following the SOLID principles and minimize coupling.
4. Conside **concerns**—aspects which can affect the code of the program. In particular, apart from the core concern (why the program was built), there are **cross cutting concerns** which end up affecting multiple parts of the code. It is important to make the code flexible and extensible
5. A good API should largely disappear from view most of the time.
6. Different extensions of the application should be possible through minimally invasive aspects or other Aspect-like tools.
7. Use standards when they add demonstrable value. Be warned that some standards hinder with the ability of the program to serve its purpose.
8. Use a domain specific language to minimize a domain concept with the code that implements it.
# Emergent Designs
1. Keep designs simple
2. A design is simple if it follows these rules, in decreasing order of priority. (Kent Beck)
	* Runs all the tests
	* Contains no duplication
	* Expresses the intent of the programmer.
	* Minimizes the number of classes and methods
# Concurrency
1. Use concurrency to decouple what gets done from when it gets done.
2. General guidelines about Concurrency to consider:
	* Concurrency can sometimes improve performance, but only when there is a lot (non-trivial amount) of wait time that can be shared between multiple threads or processors
	* Changing to a multi-threaded design demands a change in design.
	* Understanding concurrency issues remain important.
	* Concurrency incurs some overhead, both in performance, as well as additional code.
	* Correct concurrency is complex even for simple problems.
	* Concurrency bugs aren’t usually repeatable, so they are often ignored as one-offs instead of the true defects that they are
	* Concurrency demands a fundamental change in design strategy.
3. Concurrency defense principles:
	* Use the Single Responsibility Principle.. Separate concurrent code from other code
		* Concurrency related code has its own life cycle of development, change and tuning.     
		* Concurrency related code has its own challenges separate from non-concurrent code.
	* Use encapsulation: limit the access of any data that may be shared.
		* It helps prevent code from breaking when it modifies shared data.
		* It prevents duplication of effort required to make everything is thread-safe.
		* It lessens the burden on finding failures.
	* Use copies of data instead of the actual data.
	* Parition data into independent subsets that can be operated on by independent threads, possibly in different processors.
4. Know the library you are working with.
	* Use the provided thread-safe collections
	* Use the executor framework for executing unrelated tasks.
	* Use nonblocking solutions when possible.
	* Note library classes which are not thread safe.
5. Avoid using more than one method  on a shared object. Beware dependencies between synchronized models.
6. When more than one method must be used on a shared object, use the following:
	* **Client Based Locing** - client locks the server before calling the first method. The lock's extent includes the code calling the last method.
	* **Server Based Locking** - locking occurs within. The server creates a subroutine that locks the server, calls all the methods and then unlocks. Clients call this method.
	* **Adapted Server** - create an intermediary method that performs the locking
7. Keep synchronized sections as small as possible.
8. Think about shut-down code early and getting it working early.
9. Write tests that have the potential to expose problems, and then run them frequently with different programmatic configurations and system configurations and load.
	* Treat spurious failures as candidate threading issues: Do not ignore system failures as one-offs.
	* Get non-threading code to work first.
	* Make thread code pluggable so it runs in various configurations such as:
		* One thread, several threads, varied as it executes.
		* Threaded code interacts with something that can be both real or a test double.
		* Execute with test doubles that run quickly, slowly, variable.
		* Configure tests so they can run for a number of iterations.
10. Make thread code tunable. Allow for changes brought about by the system.
11. Run with more threads than processors to promote task swapping and catch deadlocks.
12. Run on different platforms early and often.
13. Instrument your code to try and force failures. Make it run code that forces it to execute threads in different orderings.
# Links
* [[Clean Code by Robert Martin]]
* [[Object Oriented Programming]]
* [[Programming]]

* [Why You Shouldn't Nest Your Code by CodeAesthetic](https://www.youtube.com/watch?v=CFRhGnuXG-4) - There are two ways to reduce nesting in code
	* Extract bits of code and refactor them to their own functions
	* Invert breaking conditions and have them break early.