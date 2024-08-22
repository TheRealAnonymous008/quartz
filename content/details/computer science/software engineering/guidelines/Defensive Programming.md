* **Defensive Programming** hinges on the recognition that programs will have problems and modifications and a smart programmer will develop code accordingly.

* *Garbage In Garbage Out is the mark of a non-secure program*. Instead, programs should either return nothing, an error message, or not allow garbage to begin with. Garbage In may be handled in the following ways:
	* Check the values of all data from external sources. 
	* Check the values of all routine input parameters. 
	* Decide how to handle bad inputs.

* The best form of defensive coding is not inserting errors in the first place

* An **assertion** is code that’s used during development—usually a routine or macro—that allows a program to check itself as it runs.
	* *Use assertions to check and document assumptions made in code*. 
	* Use assertions to flush out unexpected conditions.
	* *Assertions are executable documentation* 
	* Some guidelines for assertions:
		* Use error-handling code for conditions you expect to occur; Use assertions for conditions that should never occur.
		* Avoid putting executable code into assertions. The compiler may not compile the code inserted in the assertion.
		* Use assertions to document and verify preconditions and post-tconditions.
		* Highly robust code asserts and then handles the error anyway. We cannot assume that production code won't come with errors.

* **Exceptions** are ways code pass errors or exceptional events to the code that called it. *They can reduce complexity, but if used irresponsibly, they add complexity and make code hard to follow* 
	* Use exceptions to notify other parts of the program about errors that should not be ignored. 
	* Throw an exception only for conditions that are truly exceptional. 
		* Exceptions can break [[Object Oriented Programming|encapsulation]] and add complexity; They require the caller to know what errors the callee might throw.
	* Don’t throw an uncaught exception in a section of code if you can handle the error locally.
	* Avoid throwing exceptions in constructors and destructors unless you catch them in the same place.
	* Throw exceptions at the right level of abstraction
	* Include in the exception message all information that led to the exception
	* Avoid empty catch blocks. If unavoidable, document why the try catch is empty. 
	* Know the exceptions your library code throws.
	* Consider building a centralized exception reporter. Note that this will add coupling to the system.
	* Standardize the project's use of exceptions.
		* Throw only specific objects.
		* Create your own project specific exception class. This centralizes error handling.
		* Define the specific circumstances code is allowed to throw and catch the error, and the circumstances throws an exception that won't be handled locally.
		* Determine if a centralized exception reporter will be used.
		* Define whether exceptions are allowed in constructors and destructors
	* Consider alternatives to exceptions. 

* Consider how errors are handled. The exact techniques used for an application will depend on the nature of the application
	* Return a normal value that is known to be harmless
	* When processing a stream of data, substitute the next piece of valid data.
	* Return the same answer as the last time. 
	* Substitute the closest legal value 
	* Log a warning message to a file. When logging, make sure the log file is [[Cybersecurity|secure]]
	* Return an error code or throw an exception to be handled higher up in the program. 
	* Call an error handler object. 
		* This centralizes error handling at the cost of [[Cohesion and Coupling|coupling]] everything to the error handler. 
		* It is also unsafe to do this when  attackers compromise the address of the error handler.
	* Display an error message (but make sure not to tell too much to a potential attacker).
	* Handle the error in whatever way works best locally. 
		* This might violate encapsulation and expose parts of the code to other parts that shouldn't see them.
		* It comes with a risk to system performance, correctness and robustness.
	* Shut down. This is good for critical applications.

* **Correctness** pertains to the application never returning an inaccurate result. **Robustness** means returning a result even if it is inaccurate. *As a general rule, safety-critical applications favor correctness to robustness; general-use applications favor robustness over correctness*
* The way in which errors are handled affects the software’s ability to meet requirements related to correctness, robustness, and other nonfunctional attributes
* Unless you’ve set an architectural guideline of not checking system calls for errors, check for error codes after each call. If you detect an error, include the error number and the description of the error.

* *Use barricades to contain the damage caused by errors*. 
	* One way to barricade for defensive programming purposes is to designate certain interfaces as boundaries to “safe” areas. Data is sanitized before it leaves the interface. 
	* Convert input data to the proper type at input time (as soon as possible after it's input) .
	* Routines that are outside the barricade should use error handling because it isn’t safe to make any assumptions about the data.
	* Routines inside the barricade should use assertions, because the data passed to them is supposed to be sanitized before it’s passed across the barricade

* *The limitations of production code do not apply to the development version*. Be willing to trade speed and resource usage during development in exchange for tools that can make development go more smoothly.
	* Write debugging aids.
	* Use **offensive programming** -- handle exceptional cases in a way that makes them obvious during development and recoverable when production code is running. *Fail hard during development; Fail soft during production*.
	* Plan to remove debugging aids for production.
		* Use version control tools and build tools.
		* Use a built in preprocessor to toggle debug mode.
		* Write your own preprocessor to toggle debug mode
		* Use debugging stubs. 

* *Not all defensive programming code should be left in production*
	* Leave in code that checks for important errors.
	* Remove code that checks for trivial errors (if space is an issue)
	* Remove code that results in hard crashes or loss of data
	* Log errors for technical support personnel. 
	* Verify all error messages are in a friendly language.
	* *Too much defensive programming code in production will cause slow down*
# Links
* [[Code Complete by McConnell]]