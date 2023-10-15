# Virtual Machines
- Programming Language analogy:  
	- Each computer has a native machine language  
		(language L0) that runs directly on its hardware  
	-  A more human-friendly language is usually constructed  
		above machine language, called Language L1
- Programs written in L1 can run two different ways:  
	-  Interpretation – L0 program interprets and executes L1  
		instructions one by one  
	-  Translation – L1 program is completely translated into  
		an L0 program, which then runs on the computer  
		hardware
![[Pasted image 20230920222207.png]]
# Data Representation 
## Binary Numbers
- 1 means true 0 means false
- Left most digit is Most Significant Bit (MSB) right most bit is Least significant bit (LSB)
- e.g. 1011001010011100
- each digit is a power of representation 
- ![[Pasted image 20230920222547.png]]
#### Binary to decimal 
- dec = 2^n-1 + 2^n-2 + ... + 2^1 + 2^0
	- e.g 00001001 = 9
		- (1 x 2^3) + (1 x 2^0) = 9
#### Binary Addition
- Starting from the left add each pair
	- 1 over 1 results in a 0 with a carry of the 1 to the next number
## Hexadecimal
### Integer storage size
- Byte holds 8 bits ranging from 0 to 255
- Word holds 16 bits ranging from 0 to 65535
- Doubleword holds 32 bits randing from 0 to 4,294,969,295
- Quadword holds 64 bits ranging from 0 to 18,446,744,073,709,551,615
#### Hex Representation 
![[Pasted image 20230920223737.png]]
### Binary To Hex
- Split the binary digit into sections of 4
- E.g. 00101101010011110010100
	- turns into 1 = 0001, 6 = 0110, A = 1010, 7 = 0111, 9 = 1001, 4 = 0100
	- 16A794
### Hex to Dec
- Dec = (D3 x 16^3) + (D2 x 16^2) + (D1 x 16^1) + (D0 x 16^0)
	D represents digit
- Hex 1245 equels (1 x 16^3) + (2 x 16^2) etc... or dec 4,660
- Hex 3BA4 equels (3 x 16^3) + (11 x 16^2) + (10 x 16^1) + (4 x 16^0), or Dec 15,268
### Dec to Hex
| Division | Quotent | Remainder |
| -------- | ------- | --------- |
| 422/16   | 26      | 6         |
| 26/16    | 1       | A         |
| 1/16     | 0       | 1         |
Answer of Dec 422 = 1A6
### Hex Addition
- Devide the sum of two digits by the number base (16). The quotient becomes the carry value, and the remainder is the sum digit
6A
4B
+
B5

A+B = 21/16 = 5 carry the 1 over then 
6 + 4 + 1 = 11/B

### Subtraction 
Same thing except instead of adding 1 when theres to much take 1 from the next neighbor and add 16 to yours
75
47
-
2E

-1 from the 7 o nthe top as 5 is less then 7
16 + 5 - 7 = E/14
7-1-4 = 2

## Signed Integers
- The highest bit in indicates the sign. 1 = negative 0 = positive
	- 11110110 negative
	- 00001010 positive
- If the highest digit of a hex integer is >7 the value is negative: 8A, C5
### Forming Two's Complement
- Negative numbers are stores in two's complement notation
- Represents the additive inverse

| Starting Value                       | 0000001         |
| ------------------------------------ | --------------- |
| Step 1 Reverse the bits              | 1111110         |
| step 2 add1 to the value from step 1 | 1111110+0000001 |
| Sum: two's complement repsentation                                     |     1111111            |

Note that 0000001 + 1111111 = 0000000
### Binary Subtraction
y Subtraction
- When subtraction A - B convert B into two's complement

## Character Storage

- Character Sets
	- Standard ASCII (0-127)
	- Extended ASCII (0 - 255)
	- Unicode (0 - 65-535)
# Boolean Operation
## Boolean Algebra 
- Expression created from NOT, AND, OR
![[Pasted image 20230920230848.png]]

### Not
- Inverts a Boolean Value
### And
- Needs a double true to return true
### Or 
- needs one or the other to be true to return true
#### Operator Precedence 
![[Pasted image 20230920231055.png]]
### Truth Tables 
- A Boolean function set based on Inputs and shows all of a Boolean functions outputs 
![[Pasted image 20230920231204.png]]

![[Pasted image 20230920231237.png]]
# Basic Microcomputer Design
- Clock sync CPU operations
	- Control Unit Coordinates sequence of execution steps
	- ALU performs arithmetic and bitwise processing 
	- Memory unit works like registers but are slower
	- Processors work like a back and fourth between registers and memory storage unit
	- pins in the processor form busses
	- Data bus very fast but doesn't know what data to interact with
		- Address bus sends data to every device to let it know it needs what to listen to
![[Pasted image 20230921094108.png]]
## Clock
- Synchronize all CPU and BUS operations
- machine (clock) cycle measure time of a single operation
- clock is user to trigger event 
![[Pasted image 20230921094342.png]]
## Instruction Execution Cycle
- Fetch
	- A space in memory where a bunch of instructions are stored 
- Decode
	- Decode the instruction 
		- The processor decodes what to do (i.e. this memory needs to be added)
- Fetch operands
	-  Fetches values from memory to be stored temporarily for the 
- Execute
	- Executes the cycle
- Store Output
	-  Stores the output in memory if the value is in memory
	-  Tells the system to store it at the value it states
![[Pasted image 20230921094623.png]]

## Reading from Memory
Multiple machine cycles are required when reading from memory, because it responds much more slowly then the CPU the steps are:
	 1. Place the address of the value you want to read on the address bus.
	 2. Assert ( changing the value of) the processors RD (read pin)
	 3. Wait one clock cycle from the memory chips to respond
	 4. Copy the data from the data bus into the destination operand 
## Cache Memory
- High speed expensive static RAM both inside and outside the CPUL
		- Leel-1 Cache: inside the CPU
		-  level-2 Cache: outside the CPU
	- Cache hit: when the data we want o hit is already in cache memory
	- Cache miss: when data to be read is not in cache memory and needs to be brought in
## How a program runs
- How a program runs assuming one thread
	- Sends the program name to the OS
		- OS Searches in Dir and system path
			- if cant find fails
		- If finds it knows what to run
			- Tells the disk manager in memory run it
			- Loader tells the OS to run at the beginning of the function
			- A program may need to wait for resources and return to the OS before starting
	- There is bits that hand expectations in programs that get flipped if they happen (i.e divide by zero)
![[Pasted image 20230921101012.png]]
## IA-32
### Modes of Operation
- Protected mode
	- Native mode (windows, linux)
	- switches between tasks
- Real Address mode
	- native MS-DOS
	- Only run one thing at a time
- System management mode
	- power management, system security, diagnostics
- Virtual-mode
	- Hybrid of Protected
## Basic Execution Environment
### Addressable Memory
- Protected mode
	- 4GB of memory
	- 32-bit address
- Real-address and Virtual-8086 modes
	- 1mb space
	- 20-bit address
### General-Purpose Registers
- Named storage location inside the CPU, Optimized for speed
![[Pasted image 20230921102056.png]]
### Accessing Parts of Registers
- Use 8-bit name, 16-bit name, or 32-bit name
- Applies to EAX, EBC, ECX and EDX
![[Pasted image 20230921102258.png]]
- Some registers have only a 16-bit name for their lower half
	- Different registers call different parts of the 64bit block
	- This is all static where somewhere in your computer there is a register bank that calls all of the registers 
![[Pasted image 20230921102404.png]]
### Some Specialized Register Uses
- General-Purpose 
	- EAX - accumulator
	- ECX - loop counter
	- ESP - stack counter
	- ESI, EDI - index registers
	- EBP - extended frame pointer (stack)
- Segment
	- CS - code segment
	- DS - data segment
	- SS - stack segment
	- ES, FS, GS - additional segment
- EIP - instruction pointer
- EFLAGS
	- status and control flags
	- each flag is a single binary bit
### Status Flags
- Carry
	- unsigned arithmetic out of range
- Overflow
	- Signed arithmetic out of range
- Sign
	- Result is negative
- Zero
	- Result is zero
- Auxiliary Carry
	- Carry from bit 3 to bit 4
- Parity
	- Sum of 1 bits is an even number
## IA-32 Memory Management
### Protected Mode
- 4GB addressable RAM
- Designed for multitasking
- Each program is assigned a memory partition 

### 64-Bit Processors
- 64-Bit Operation Modes
	- Compatibility Mode - can run existing 16-bit and 32-bit applications (Only supports 32-bit apps in this mode)
	- 64-bit mode - Windows 64 uses this
- Basic Execution Environment
	- Addresses can be 64 bits
## 64-Bit General Purpose Registers
- 32-bit general purpose registers:  
	-  EAX, EBX, ECX, EDX, EDI, ESI, EBP, ESP, R8D, R9D,  
		R10D, R11D, R12D, R13D, R14D, R15D  
-  64-bit general purpose registers:  
	- RAX, RBX, RCX, RDX, RDI, RSI, RBP, RSP, R8, R9,  
		R10, R11, R12, R13, R14, R15

## Components of an IA-32 Microcomputer
