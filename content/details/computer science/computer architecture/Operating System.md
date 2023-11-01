* **Operating Systems** are the interface between the computer hardware and the computer software that serves to allocate resources and manage the execution of programs and I/O devices.
	* They are the programs running at all times called the **kernel**, alongside **system programs**. 
	* They may also include **middleware**  - frameworks that provide additional services to application developers.
	* Typically , they have **device drivers** that interfaces between the OS and any device on the computer such that the device can compete with the CPU for memory access, necessitating a need for memory control.
## Bootstrap
* A **bootstrap program** loads the OS when the system is first loaded.  The bootstrap program starts running the kernel. 
* Other system programs called **daemons** are ran while the kernel is running. 
## Interrupts
* An event can raise an **interrupt**. When the [[Computer Processors|processor]] is interrupted, *execution is transferred to a location in the system, allowing asynchronous processing*. 
	* Interrupts include hardware interrupts (raised by hardware) or exceptions (raised by software due to an error).
	* Interrupts may be raised using a **system call**, a request from a user program that an OS service be performed. 
	* The CPU timer can also raise an interrupt when control has not been passed back to the kernel. This is treated as a fatal error.

* We index interrupts with an **interrupt vector** - a table of addresses.
* **Interrupt chaining** involves having each interrupt vector point to the head of a list of interrupt handlers. When the interrupt is raised, the list is searched for a handler that can service the request. 
* The general flow for interrupts is as follows:
	* Device *raises* interrupt detected on the interrupt request line (nonmaskable for critical tasks and maskable otherwise).
	* CPU *catches* the interrupt and *dispatches* to the interrupt handler routine.
	* Handler *clears* the interrupt:
		* Save any state changed.
		* Determine interrupt cause.
		* Perform processing.
		* Perform state 
		* Return to execution state prior to interrupt
* Modern hardware (via CPU and **interrupt-controller hardware** provides additional features)
	* Deferring interrupt handling during critical processing
	* Dispatching to proper interrupt handler.
	* Multilevel interrupts to distinguish based on priority and urgency via **Interrupt priority levels**.
## Security
* We distinguish between two modes -- **user mode** where tasks are executed on behalf of the user, and **kernel mode** where tasks are executed on behalf of the OS. This gives **privilege** to only certain users. 
* We may have **protection rings** to add more intermediate modes with varying levels of privileges. 
* Virtualization also comes with a **virtual machine manager** that runs at a higher privilege than user mode but lower than kernel mode.
## Resource Management
* *The OS is a resource manager*.
* It manages the different *processes*, especially if they are to occur concurrently.
* It manages *allocation* as processes require allocated memory to be loaded and executed. Memory must also be released when processes are finished.
* It manages *files* which serve as means of storing data. This roles includes creating, and deleting files, as well as mapping them onto mass storage.
* It manages the *mass storage* to store files on hardware.
* It manages the *[[Cache Memory]]* to facilitate fast read and write operations using cache memory, which is inherently limited by size and so requires replacement. 
	* This includes **cache coherency** to maintain consistent copies of data across the memory hierarchy.
* It manages *I/O systems* to abstract input and output via driver interfaces.
* It maintains *security* by managing the allowed operations of users.
* It allows for **virtualization** - abstracting away hardware as if running another OS within itself.
* It may regulate operations within a *network* via distributed computing.
# Topics
* [[Multiprogramming]]

# Links
* [[Operating System Concepts by Silberschatz, Galvin, and Gagne|Silberschatz Ch. 1]]

* [[Computer Organization]]