# Calling Conventions
* A **Calling Convention** governs how functions on a particular architecture and operating system interact.
* Calling conventions *ensure that functions compiled by different compilers can interoperate*, and they ensure that operating systems can run code from different programming languages and compilers.
* The **Caller*  is the function that calls another function. It is not the currently running function
* The **Callee** is the function that was called. It is the currently executing function.
# Terms
* **Call stack** - a stack that stores information about the active subroutines in a computer program
	* Identifies the address of the subroutine the current function should return to once it is finished executing.
	* Stack grows downward by convention, so that pushes decrement the pointer.
* **Memory Heap** - pertains to a location in memory wherein data is manually allocated and deallocated. 
	* Allows for persistent, variable sized data.
	* May introduce memory leaks.
	* Usually segmented, and so access is slower.
* **Call Preserved Registers** - holds values that are preserved.
	* It is the callee's responsibility to push these on the stack.
	* A callee may use these registers but it must restore them to their original values before returning.
* **Call Clobbered** - holds temporary quantities that need not be preserved across instruction calls
	* It is the caller's responsibility to save these variables explicitly and restore it when the function resumes.
	* The caller allows the callee to modify the value as necessary, and only then will it save the value.
	* From the callee's point of view, it knows that it can freely modify this value without saving since it is not responsible for saving any values, only performing the logic.

* **Stack Pointer*** - a register that stores the memory address of the last data element added to the stack.
	* Any values above the stack pointer are call preserved
	* Any values below the stack pointer are call clobbered.
```
    | values here were placed by callers 
fp  | values here are allocated by callees
... | ...
sp  | return address
```

* **Frame pointer*** - used to keep track of the current stack frame.   It is used to keep track of procedure calls so that the callee can return to the correct caller.
	* It's unreliable to simply rely on the stack pointer since it may change with every allocation. 
	* The frame pointer acts as a constant base address for the current function being executed.

* **Program Counter*** - a register that contains the address of the instruction that is being executed at the current time.
	* As instructions are fetched, it is incremented by 1.


# Pipeline
* The following describes the general low-level processes that occur when we call a subroutine
* Let `foo(x)` be the function we are calling. The caller is `main()`.
* Denote `fp` as the frame pointer and `sp` as the stack pointer

## Before Calling
#### Stack State
```
main frame |  main's frame 
--------------------------
sp         | top of the stack
```

## Just Before Execution
#### Stack State
```
fp         |
main frame |  main's frame 
--------------------------
           |  arg x
sp         |  return address 
```
#### Events
Control is with `main` (the caller).
1. Push arguments on the call stack
2. Push the return address on the call stack.
3. Save  call clobbered
4. Jump to the called function 
5. Update the program counter

## Entering Callee
#### Stack State
```
main frame |  main's frame 
--------------------------
           |  arg x
           |  return address 
	       |  saved fp
fp	       |  local variables
           |
sp         |  --- top of stack --
```
#### Events
1. Save the old `fp` by pushing it onto the call stack.
2. `F` resets `fp` to the current `sp`
3. Save call preserved
4. Allocate local variables by decrementing the stack pointer.

## Exiting Callee
#### Stack State
```
fp         |
main frame |  main's frame 
--------------------------
sp         |  arg x
```
#### Events
1. Restore Call-preserved register
2. Deallocate everything off the stack by setting `sp` to where `fp` points at.  Remember this contains the saved old frame pointer.
3. Set `fp` to the value pointed to by `sp` and pop the stack.
4. Return to the caller using the return address that `sp` is now pointing to. Pop the stack.

## Entering Caller
#### Events
1. Restore Call-clobbered registers.
2. Inspect arguments that were passed back since they are still accessible.