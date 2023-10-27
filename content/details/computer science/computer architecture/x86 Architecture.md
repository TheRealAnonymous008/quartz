# Registers
* Being CISC, we only have  a few registers

* We have $4$ general registers. `EAX`, `EBX`, `ECX`, `EDX`.  These are the 32 bit registers.
* We may further break them down into 16 bit registers as `AX`, `BX`, `CX` and `DX`.  These are the lower 16 bits of the above registers
* The above can be broken down into two 8 bit registers. The lower 8 bits correspond to those with suffix `L`, and the upper correspond to the suffix `H`. We thus have `AL`, `BL`. `CL`, `DL` and `AH`, `BH`. `CH`, `DH`. 
* While not strictly enforced, there is a suggested way to use these registers

### General Registers
* **EAX: Accumulator** - Use this for I/O port access, arithmetic, interrupt calls, and others.
* **EBX: Base** - Use this as a base pointer for memory access. It may also interrupt return values.
* **ECX: Counter** Use this as a loop counter and for shifting. 
* **EDX:  Data** Use this for I/O port access, arithmetic, and interrupts

### Segment Registers
* The segment register *holds the segment address of various items*. These are only available in $16$ bit. 
* **CS: Code Segment** - This holds the code segment in which the program runs. Changing this might cause a hang.
* **DS: Data Segment** - This holds the data segment that your program accesses. Changing this might give erroneous data.
* **ES, FS, GS: Extras** - Extra segment registers for pointer addressing (i.e., for VRAM). 
* **SS: Stack Segment** Holds the stack ]segment that the program uses. 

### Indexes and Pointers
* These are registers that are an address. 
* **EDI, DI: Destination** - The destination index register. Used for string memory array copying and setting for far pointer addressing with ES.
* **ESI, SI: Source** The source index register. Used for string and memory array copying.
* **EBP, BP: Base Pointer** - Holds the frame pointer of the stack
* **ESP, SP: Stack Pointer** - Holds the top address of the stack pointer
* **EIP, IP: Index Pointer** -Holds the offset of the next instruction.

### EFLAGS
* The EFLAGS register *holds the state of the processor.* Each bit specifies the specific parameter of the last instruction.
* The initial value of EFLAGS is set to $0x00000002$

| Bit| Label | Description |  Function | 
|---|---|---| --- |
| 0 | CF | Carry | Set if there is a carry out or borrow-in from the MSB | 
| 1 | -- | -- |
| 2 | PF | Parity | Tests the lower byte if it has an even parity |
| 3 | -- | -- |
| 4 | AF | Auxiliary Carry| Tests the lower byte to see if there is a carry-out or borrow-in from the lower to the higher nibble |
| 5 | -- | -- |
| 6 | ZF | Zero | Set if the result is zero |
| 7 | SF | Sign | Set to the MSB of the result |
| 8 | TF | Trap | 
| 9 | IF | Interrupt Enable |
| 10 | DF | Direction | Determines the direction in which string operations will occur. Set if it auto-decrements. Clear if auto-increments | 
| 11 | OF | Overflow | Set if the signed result overflows | 
| 12-13 | IOPL | I/O Privilege Label |
| 14 | NT | Nested Task |
| 15 | -- | -- |
| 16 | RF | Resume |
| 17 | VM | Virtual 8080 mode |
| 18 | AC | Alignment Check |
| 19 | VIF | Virtual Interrupt |
| 20 | VIP | Virtual Interrupt Pending| 
| 21 | ID | ID |
| 22-31 | -- | -- |
Those that have blank entries are reserved registers.
# Variables
All variables are declared in `.data`

|Directives|Description|
|---|---|
|.byte|8 bit integer|
|.half|16-bit integer|
|.word|32-bit integer|
|.dword| 64-bit integer|
|.float| 32-bit single precision floating point|
|.double|64-bit double precision floating point|
|.asciz| string with null terminator|

All memory locations are viewed as 1 byte with Littel Endian ordering and 32-bit words for a 32-bit system.

Memory is used for composite data such as arrays and structures

# Addressing Modes
* **Immediate Addressing** - generate a memory address by looking at the value of the immediate specified in the instruction 
* **Register Addressing** - use the value stored in register as a memory address
* **Base Addressing** - add an immediate to a register value to create a memory address.
* **PC-relative addressing** - add an immediate to the program counter.
* **Memory Addressing Mode** - operand is in memory so it is accessed via an offset.
	* The offset can be done using the following components:
		1. Displacement - an 8, 16 or 32-bit value
		2. Base - the value in a general purpose register. Must be 32 bit.
		3. Index - the value in a general purpose register. Must be 32 bit.
		4. Scale factor - A value that is multiplied to the index value.
	* The offset is then calculated as 

$$
\text{offset} = \text{base} +\text{index}\times \text{scale} +\text{displacement}
$$

#### General Rules
1. Operands MUST have their data sizes match. 
2. Immediate operands are only used as the source operands.
3. Memory-to-Memory operations are not supported.
4. If the operand is a combination of memory address mode, and immediate addressing mode, a prefix must be used (`byte`, `word` or `dword`).
5. The `ESP` register cannot be used as an index register
6. Scale factors can only be used with the index registers. 
# Instructions
* A complete instruction set is found [here](https://www.cs.virginia.edu/~evans/cs216/guides/x86.html)