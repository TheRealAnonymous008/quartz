* An **Instruction Set Architecture** is a specification that defines the set of supported instructions, data types, registers, memory management schemes, addressing modes, virtual memory, and I/O models. 
* It acts as an interface between software and hardware.
# Design Principles
* *Simplicity Favors Regularity*  - regularity makes the implementation simpler. Simplicity enables higher performance at a lower course.
* *Smaller is faster* - If we have smaller data to work with, we only need a few bits to read, write and move data around.
	* Favor registers instead of memory especially when performing loads and stores.
* *Make the common case fast* to maximize performance.
* *Good design demands good compromise* - A well-designed system will require us to be flexible, and if we bind ourselves to just one standard, the architecture will be limited. However, we ought to be smart when introducing complexity.
# Terms
### Instructions
* Instructions consist of two parts a **mnemonic** - the symbolic name of an instruction and **operands** that act as inputs to the instructions
* **Opcode** pertains to a portion of an instruction (usually in binary) that specifies the operation to be performed 
* An **immediate operand** is an operand that is directly encoded in the instruction. 
	* It helps when we don't want to perform load for the common case of having known constants.

* **Load** generally pertains to moving data from memory to register.
* **Store** generally pertains to moving data from register to memory.

* A **basic block** - is a sequence of instructions with no branches out (except at the end) and no branches in (except at the beginning)
	* *All instructions in a block are executed in sequence*.
	* *No instruction executes between two instructions in a sequence*. 
	* Can be (ideally) optimized by the compiler.
### Addressing
* An **address space** defines a range of discrete addresses such that each may correspond to a logical or physical entity 
* An **addressing mode** pertains to specifications on how machine language instructions identify the operands of each instruction by calculating the effective memory address of an operand.
### Memory
* A **register** is *a quickly accessible location that is available in the processor*. It is a small but fast storage that may be used for smaller, frequently performed operations.
	* The **register file** is just an array of registers in a processor
* **Memory** pertains to a device or system that is used to store information for immediate use for a computer. 
* The **memory address** is a reference to a specific location in memory
	* It can be the **physical address** - the physical location in memory 
	* It can also be the **logical address** which is a mapping to the physical location
* **Memory Alignment** - refers to how data in memory is arranged. 
	* *It concerns accessing data in the proper units*.
### Quantities
* The **cycle time** is the time per cycle.
	* determines the worst case propagation time through gates that produce a signal required in the next cycle
* The **performance equation** can be used to analyze performance.

$$
\frac{\text{time}}{\text{program}} =\frac{\text{time}}{\text{cycles}} \times \frac{\text{cycles}}{\text{instructions}} \times \frac{\text{instructions}}{\text{program}} 
$$

# Variants
## Reduced Instruction Set Computer
* An instruction set which reduces the number of cycles per instruction but increases the number of instructions per program
### Characteristics
* *Has More Instructions*
	* Instructions themselves are simple, do only one thing and are typically primitive.
	* Each RISC instruction is encoded in a fewer number of bits (generally a 32-bit encoding for 4 bytes)
* *Pipelining*
* *Single Clock Cycle* 
	* Each instruction executes in an equal number of clock cycles, and this number is minimized per the specifications of this architecture.
	* This enables Pipelining as discussed above.
* **Load and Store Architecture**
	* Operands that are in the memory must be loaded  first in the registers before any arithmetic and logic execution could proceed, and the result is stored back to memory.
* No operations can be performed on memory itself*. *All operations must be performed via the register* There is no need to reload data into memory every time.
* *Transistors are spent on memory registers* Hence, more registers are available for the programmer.
* Instructions are encoded with a fixed number of bits
* Emphasis on the software of the system.



## Complex Instruction Set Computer
* An instruction set which minimizes the number of instructions per program but at the cost of the number of cycles per instructions
### Characteristics
* *Has a lot of instructions*
	* Some of these instructions are complex in that they operate directly on the memory banks without the programmer needing to explicitly call any loading or storing functions. 
* *Multi-Clock Instructions*
	* The instructions themselves may execute in different clock cycles depending on the complexity of the instruction.
* Supports Many Addressing Modes
* Allows register and memory- operands at the same time
* FLAG registers may be used for control flow or conditional code.
* Emphasis on the hardware of the system
* Transistors of the system are used for storing complex instructions directly in the hardware.
	* This means that there are less transistors that can be reserved for registers.

# Topics
* [[RISC-V]]
* [[x86 Architecture]]
* [[Procedure Calling Workflow]]