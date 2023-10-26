# Registers
* In a 32-bit system, we may have 32 integer registers and 32 floating-point register.

### Integer registers

| Register Name | ABI | Name | Description | Saved by Calle- | 
|---|---|---|---|
| x0 | zero | Always Zero  |  |
| x1 | ra | Return address | R |
| x2 | sp | Stack Pointer | E |
| x3 | gp | Global pointer |  |
| x4 | tp | Thread pointer |  |
| x5 | t0 | Temporary / Alternate Return Address | R |
| x6 - x7 | t1 - t2 | Temporary | R |
| x8 | s0 / fp | Saved register / Frame Pointer | E |
| x9 | s1 | Saved Register | E |
| x10 - x11 | a0 - a1 | Function argument / return value | R |
| x12 - x17 | a2 - a7 | Function argument | R |
| x18 - x27 | s2 - s11 | Saved Register | E |
| x28 - x31 | t3 - t6 | Temporary | R |

* **Always Zero** is Hardwired to always be zero. Any value moved to this register is discarded and zero outputted in its place.

### Floating point registers
| Register Name | ABI Name | Description | Owner | 
|---|---|---|---|
| f0 - f7 | ft0-7 | Temporaries | R  |
| f8 - f9 | fs0-1 | Saved Registers | E |
| f10 - f11 | fa0-1 | Arguments / Return values | R |
| f12 - f17 | fa2-7 | Arguments | R |
| f18 - f27 | fs2-11 | Saved Registers | E |
| f28 - f31 | ft8-11 | Temporaries | R |

* Note: We have multiple registers for return values in ode to support returning 64-bit values.
* We reserve register `a7` typically for I/O (i.e., how to render output).

# Variables
* All variables are declared in `.data`

|Directives|Description|
|---|---|
|.byte|8 bit integer|
|.half|16-bit integer|
|.word|32-bit integer|
|.dword| 64-bit integer|
|.float| 32-bit single precision floating point|
|.double|64-bit double precision floating point|
|.asciz| string with null terminator|

* All memory locations are viewed as 1 byte with Little Endian ordering and 32-bit words for a 32-bit system.
* Memory is used for composite data such as arrays and structures

# Addressing Modes
* **Immediate Addressing** - generate a memory address by looking at the value of the immediate specified in the instruction 
* **Register Addressing** - use the value stored in register as a memory address
* **Base Addressing** - add an immediate to a register value to create a memory address.
* **PC-relative addressing** - add an immediate to the program counter.

# Instructions
* A complete instruction set is found [here](https://msyksphinz-self.github.io/riscv-isadoc/html/index.html). Pseudo-instructions [here](https://michaeljclark.github.io/asm.html).
* Some additional standards to look out for: Multiplication, Division, and Floating Point.

### Instruction Types
* **R-type** 
```
funct7 | rs2 | rs1 | funct3 | rd | opcode
  7    |  5  |  5  |   3    |  5 |   7     
```
* **I-type** 
```
immediate | rs1 | funct3 | rd | opcode | 
   12     |  5  |    3   | 5  |   7    |
```
* **S-type***
```
imm(11:5) | rs2 | rs1 | funct3 | imm(4:0) | opcode
    7     |  5  |  5  |   3   |     5     |    7  
```
* **Shift Type***
```
funct6   |   immed   | rs1  | funct3 | rd | opcode 
   6     | 6 sign ext. | 5  |   3    |  5 |    7
```
# Procedure Calling
In order to call a procedure using RISC-V we need to do the following
1. Place the parameters in the `a0` to `a7` registers. This is to ensure that we do not lose any parameters.
2. Transfer control to the procedure. We do this using the `JAL` and the `JALR` instructions.
3. Acquire storage for procedure
4. Perform the procedure
5. Place the result in register for caller
6. Return to the address of the caller (i.e., the address in `ra`)


# Links
* [Computer Organization and Architecture (RISC-V) EECS2021E by Amir Ashouri](https://www.youtube.com/watch?v=ucUHpSYm08U&list=PL-Mfq5QS-s8iUJpNzCOtQKRfpswCrPbiW) - lecture series on computer organization and architecture