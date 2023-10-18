#Basics
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
#Data
## Binary Numbers
#Binary
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
#Hex
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
#char

- Character Sets
	- Standard ASCII (0-127)
	- Extended ASCII (0 - 255)
	- Unicode (0 - 65-535)
# Boolean Operation
#Bool
## Boolean Algebra 
#Math
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
#Memory
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
#IA-32
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
#64bit

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

# Basic Elements of Assembly Language
#Basics 
# Integer Constants 
• Optional leading + or – sign  
• binary, decimal, hexadecimal, or octal digits  
• Common radix characters:  
– h – hexadecimal  
– d – decimal  
– b – binary  
– r – encoded real  
Examples: 30d, 6Ah, 42, 1101b  
Hexadecimal beginning with letter: 0A5h
![[Pasted image 20231015193742.png]]

## Character and String Constants
-  Enclose character in single or double quotes  
-   'A', "x"  
-  ASCII character = 1 byte  
-  Enclose strings in single or double quotes  
-  "ABC"  
-  'xyz'  
-  Each character occupies a single byte  
-  Embedded quotes:  
-  'Say "Goodnight," Gracie'  
Character and String Constants 

## Directives
• Commands that are recognized and acted upon  
by the assembler  
– Not part of the Intel instruction set  
– Used to declare code, data areas, select memory  
model, declare procedures, etc.  
– not case sensitive  
• Different assemblers have different directives  
– NASM not the same as MASM, for example

## Instructions
• Commands that are recognized and acted upon  
by the assembler  
– Not part of the Intel instruction set  
– Used to declare code, data areas, select memory  
model, declare procedures, etc.  
– not case sensitive  
• Different assemblers have different directives  
– NASM not the same as MASM, for example     

## Label
• Act as place markers  
– marks the address (offset) of code and data  
• Follow identifer rules  
• Data label  
– must be unique  
– example:myArray (not followed by colon)  
• Code label  
– target of jump and loop instructions  
– example: L1: (followed by colon)

## Mnemonics and Operands
• Instruction Mnemonics  
– memory aid  
– examples: MOV, ADD, SUB, MUL, INC, DEC  
• Operands  
– constant  
– constant expression  
– register  
– memory (data label)  
Constants and constant expressions are often  
called immediate values

## Comments
• Comments are good!  
– explain the program's purpose  
– when it was written, and by whom  
– revision information  
– tricky coding techniques  
– application-specific explanations  
• Single-line comments  
– begin with semicolon (;)
• Multi-line comments  
– begin with COMMENT directive and a programmer-  
chosen character  
– end with the same programmer-chosen character

## Instructions Format Examples
• No operands  
– stc ; set Carry flag  
• One operand  
– inc eax ; register  
– inc myByte ; memory  
• Two operands  
– add ebx,ecx ; register, register  
– sub myByte,25 ; memory, constant  
– add eax,36 * 25 ; register, constant-expression

## Example: Adding and Substracting Integers
; AddTwo.asm – adds two 32-bit integers  
.386  
.model flat,stdcall  
.stack 4096  
ExitProcess PROTO, dwExitCode:DWORD  
.code  
main PROC  
mov eax,5 ; move 5 to the EAX register  
add eax,6 ; add6 to the EAX register  
INVOKE ExitProcess,0  
main ENDP  
END main

## Program Template
; Program Template (Template.asm)  
; Program Description:  
; Author:  
; Creation Date:  
; Revisions:  
; Date:Modified by:  
.386  
.model flat,stdcall  
.stack 4096  
ExitProcess PROTO, dwExitCode:DWORD  
.data  
; declare variables here  
.code  
main PROC  
; write your code here  
INVOKE ExitProcess,0  
main ENDP  
; (insert additional procedures here)  
END main

## Assembly-Link Execute Cycle
• The following diagram describes the steps from  
creating a source program through executing the  
compiled program.  
• If the source code is modified, Steps 2 through 4  
must be repeated.
![[Pasted image 20231015200114.png]]

## Intrinsic Data Types
• BYTE, SBYTE  
– 8-bit unsigned integer; 8-bit signed integer  
• WORD, SWORD  
– 16-bit unsigned & signed integer  
• DWORD, SDWORD  
– 32-bit unsigned & signed integer  
• QWORD  
– 64-bit integer  
• TBYTE  
– 80-bit integer
• REAL4  
– 4-byte IEEE short real  
• REAL8  
– 8-byte IEEE long real  
• REAL10  
– 10-byte IEEE extended real

## Data Definition Statement
• A data definition statement sets aside storage in  
memory for a variable.  
• May optionally assign a name (label) to the data  
• Syntax:  
[name] directive initializer [,initializer] . . .  
value1 BYTE 10  
• All initializers become binary data in memory

## Defining BYTE and SBYTE Data
value1 BYTE 'A' ; character constant  
value2 BYTE 0 ; smallest unsigned byte  
value3 BYTE 255 ; largest unsigned byte  
value4 SBYTE -128; smallest signed byte  
value5 SBYTE +127 ; largest signed byte  
value6 BYTE ? ; uninitialized byte

list1 BYTE 10,20,30,40  
list2 BYTE 10,20,30,40  
BYTE 50,60,70,80  
BYTE 81,82,83,84  
list3 BYTE ?,32,41h,00100010b  
list4 BYTE 0Ah,20h,‘A’,22h

## Defining Strings
- A string is implemented as an array of characters  
	– For convenience, it is usually enclosed in quotation marks  
	– It often will be null-terminated
-  Examples:  
str1 BYTE "Enter your name",0  
str2 BYTE 'Error: halting program',0  
str3 BYTE 'A','E','I','O','U'  
greeting BYTE "Welcome to the Encryption Demo  
program "  
BYTE "created by Kip Irvine.",0
• To continue a single string across multiple lines, end  
each line with a comma:  
menu BYTE "Checking Account",0dh,0ah,0dh,0ah,  
	"1. Create a new account",0dh,0ah,  
	"2. Open an existing account",0dh,0ah,  
	"3. Credit the account",0dh,0ah,  
	"4. Debit the account",0dh,0ah,  
	"5. Exit",0ah,0ah,  
	"Choice> ",0
• End-of-line character sequence:  
	– 0Dh = carriage return  
	– 0Ah = line feed  
str1 BYTE "Enter your name: ",0Dh,0Ah  
BYTE "Enter your address: ",0  
newLine BYTE 0Dh,0Ah,0

## Using the DUP Operator
• Use DUP to allocate (create space for) an array or  
string. Syntax: counter DUP (argument)  
• Counter and argument must be constants or  
constant expressions  
var1 BYTE 20 DUP(0) ; 20 bytes, all equal to zero  
var2 BYTE 20 DUP(?) ; 20 bytes, uninitialized  
var3 BYTE 4 DUP("STACK"); 20 bytes:  
"STACKSTACKSTACKSTACK"  
var4 BYTE 10,3 DUP(0),20; 5 bytes

## Defining WORD and SWORD Data
• Define storage for 16-bit integers  
– or double characters  
– single value or multiple values  
word1WORD65535 ; largest unsigned value  
word2SWORD –32768 ; smallest signed value  
word3WORD? ; uninitialized, unsigned  
word4WORD"AB" ; double characters  
myList WORD1,2,3,4,5 ; array of words  
arrayWORD5 DUP(?) ; uninitialized array

## Defining DWORD and SDWORD Data
• Define storage for 16-bit integers  
– or double characters  
– single value or multiple values  
word1WORD65535 ; largest unsigned value  
word2SWORD –32768 ; smallest signed value  
word3WORD? ; uninitialized, unsigned  
word4WORD"AB" ; double characters  
myList WORD1,2,3,4,5 ; array of words  
arrayWORD5 DUP(?) ; uninitialized array

## Defining QWORD, TBYTE, Real Data
Storage definitions for quadwords, tenbyte values,  
and real numbers:  
quad1 QWORD1234567812345678h  
val1TBYTE 1000000000123456789Ah  
rVal1 REAL4 -2.1  
rVal2 REAL8 3.2E-260  
rVal3 REAL10 4.6E+4096  
ShortArray REAL4 20 DUP(0.0)  
Defining QWORD, TBYTE, Real Data

## Little Endian Order
• All data types larger than a byte store their  
	individual bytes in reverse order. The least  
	significant byte occurs at the first (lowest) memory  
	address.  
• Example:  
val1 DWORD 12345678h
![[Pasted image 20231015201944.png]]

## Adding Variables to AddSub
````gas
TITLE Add and Subtract, Version 2(AddSub2.asm)  
; This program adds and subtracts 32-bit unsigned  
; integers and stores the sum in a variable.  
INCLUDE Irvine32.inc  
.data  
val1 DWORD 10000h  
val2 DWORD 40000h  
val3 DWORD 20000h  
finalVal DWORD ?  
.code  
main PROC  
mov eax,val1 ; start with 10000h  
add eax,val2 ; add 40000h  
sub eax,val3 ; subtract 20000h  
mov finalVal,eax ; store the result (30000h)  
call DumpRegs ; display the registers  
exit  
main ENDP  
END main
````

## Declaring Unitialized Data
Advantage: the program's EXE file size is reduced.  
• Use the .data? directive to declare an unintialized  
data segment:  
.data?  
• Within the segment, declare variables with "?"  
initializers:  
smallArray DWORD 10 DUP(?)

## Equal-Sign Directive
• name = expression  
• expression is a 32-bit integer (expression or constant)  
• may be redefined  
• name is called a symbolic constant  
• good programming style to use symbols  
COUNT = 500  
.  
.  
mov ax,COUNT

## Calculating the Size of a Byte Array
current location counter: $  
– subtract address of list  
– difference is the number of bytes  
list BYTE 10,20,30,40  
ListSize = ($ - list)

## Calculating the Size of a Word Array
Divide total number of bytes by 2 (the size of a  
word)  
list WORD 1000h,2000h,3000h,4000h  
ListSize = ($ - list) / 2

## Calculating the Size of a Doubleword Array
Divide total number of bytes by 4 (the size of a  
doubleword)  
list DWORD 1,2,3,4  
ListSize = ($ - list) / 4

## EQU Directive
• Define a symbol as either an integer or text  
expression.  
• Cannot be redefined  
PI EQU <3.1416>  
pressKey EQU <"Press any key to continue...",0>  
.data  
prompt BYTE pressKey

## TEXTEQU Directive
• Define a symbol as either an integer or text expression.  
• Called a text macro  
• Can be redefined  
continueMsg TEXTEQU <"Do you wish to continue (Y/N)?">  
rowSize = 5  
````
.data  
prompt1 BYTE continueMsg  
count TEXTEQU %(rowSize * 2) ; evaluates the expression  
setupAL TEXTEQU <mov al,count>  
.code  
setupAL ; generates: "mov al,10"
````

## 64-Bit Programming
MASM supports 64-bit programming, although the  
following directives are not permitted:  
– INVOKE, ADDR, .model, .386, .stack  
– (Other non-permitted directives will be introduced in  
later chapters)

## 64-Bit Version of AddTwoSum
````
1: ; AddTwoSum_64.asm - Chapter 3 example.  
3: ExitProcess PROTO  
5: .data  
6: sum DWORD 0  
8: .code  
9: mainPROC  
10: moveax,5  
11: addeax,6  
12: movsum,eax  
13:  
14: movecx,0  
15: call ExitProcess  
16: main ENDP  
17: END
````


## Things to Notice about the previous Slide
• The following lines are not needed:  
.386  
.model flat,stdcall  
.stack 4096  
• INVOKE is not supported.  
• CALL instruction cannot receive arguments  
• Use 64-bit registers when possible

# Data Transfers, Addressing,  and Arithmetic

## Operand Types
• Immediate – a constant integer (8, 16, or 32 bits)  
– value is encoded within the instruction  
• Register – the name of a register  
– register name is converted to a number and encoded  
within the instruction  
• Memory – reference to a location in memory  
– memory address is encoded within the instruction, or a  
register holds the address of a memory location

## Instruction Operand Types
![[Pasted image 20231016131731.png]]

## Direct Memory Operands
• A direct memory operand is a named reference to  
storage in memory  
• The named reference (label) is automatically  
dereferenced by the assembler
![[Pasted image 20231016131906.png]]

## MOV Instruction
• Move from source to destination. Syntax:  
MOV destination,source  
• No more than one memory operand permitted  
• CS, EIP, and IP cannot be the destination  
• No immediate to segment moves
![[Pasted image 20231016132203.png]]

## Zero Extension
When you copy a smaller value into a larger  
destination, the MOVZX instruction fills (extends)  
the upper half of the destination with zeros.
![[Pasted image 20231016132244.png]]

## Sign Extension
The MOVSX instruction fills the upper half of the  
destination with a copy of the source operand's sign  
bit.
![[Pasted image 20231016132317.png]]

## XCHG Instruction
XCHG exchanges the values of two operands. At least one  
operand must be a register. No immediate operands are  
permitted.

.data  
var1 WORD 1000h  
var2 WORD 2000h  
.code  
xchg ax,bx ; exchange 16-bit regs  
xchg ah,al ; exchange 8-bit regs  
xchg var1,bx ; exchange mem, reg  
xchg eax,ebx ; exchange 32-bit regs  
xchg var1,var2 ; error: two memory operands

## Direct-Offset Operands
A constant offset is added to a data label to produce  
an effective address (EA). The address is  
dereferenced to get the value inside its memory  
location.

.data  
arrayB BYTE 10h,20h,30h,40h  
.code  
mov al,arrayB+1 ; AL = 20h  
mov al,[arrayB+1] ; alternative notation

A constant offset is added to a data label to produce  
an effective address (EA). The address is  
dereferenced to get the value inside its memory  
location.

## Direct-Offset Operands
.data  
arrayW WORD 1000h,2000h,3000h  
arrayD DWORD 1,2,3,4  
.code  
mov ax,[arrayW+2] ; AX = 2000h  
mov ax,[arrayW+4] ; AX = 3000h  
mov eax,[arrayD+4] ; EAX = 00000002h

## INC and DEC substractions  
• Add 1, subtract 1 from destination operand  
– operand may be register or memory  
• INC destination  
– Logic: destination  destination + 1  
• DEC destination  
– Logic: destination  destination – 1

### Examples
```
.data  
myWord WORD 1000h  
myDword DWORD 10000000h  
.code  
inc myWord ; 1001h  
dec myWord ; 1000h  
inc myDword ; 10000001h  
mov ax,00FFh  
inc ax ; AX = 0100h  
mov ax,00FFh  
inc al ; AX = 0000h
```
## Add and Sub Substractions
• ADD destination, source  
– Logic: destination  destination + source  
• SUB destination, source  
– Logic: destination  destination – source  
• Same operand rules as for the MOV instruction

### Examples
```
.data  
var1 DWORD 10000h  
var2 DWORD 20000h  
.code ; ---EAX---  
mov eax,var1 ; 00010000h  
add eax,var2 ; 00030000h  
add ax,0FFFFh ; 0003FFFFh  
add eax,1 ; 00040000h  
sub ax,1 ; 0004FFFFh
```

## Negate Instructions
Reverses the sign of an operand. Operand can be a  
register or memory operand.
```
.data  
valB BYTE -1  
valW WORD +32767  
.code  
mov al,valB ; AL = -1  
neg al ; AL = +1  
neg valW ; valW = -32767
```
Suppose AX contains –32,768 and we apply NEG to it.  
Will the result be valid?

## NEG Instruction and the Flags
The processor implements NEG using the following  
internal operation:  
SUB 0,operand  
Any nonzero operand causes the Carry flag to be set

```
.data  
valB BYTE 1,0  
valC SBYTE -128  
.code  
neg valB ; CF = 1, OF = 0  
neg [valB + 1] ; CF = 0, OF = 0  
neg valC ; CF = 1, OF = 1
```

## Implementing Arithmetic Expressions
HLL compilers translate mathematical expressions  
into assembly language. You can do it also. For  
example:  
Rval = -Xval + (Yval – Zval)

```
Rval DWORD ?  
Xval DWORD 26  
Yval DWORD 30  
Zval DWORD 40  
.code  
mov eax,Xval  
neg eax ; EAX = -26  
mov ebx,Yval  
sub ebx,Zval ; EBX = -10  
add eax,ebx  
mov Rval,eax ; -36
```

## Flags Affected by Arithmetic
• The ALU has a number of status flags that reflect  the outcome of arithmetic (and bitwise) operations  
	– based on the contents of the destination operand  
• Essential flags:  
	– Zero flag – set when destination equals zero  
	– Sign flag – set when destination is negative  
	– Carry flag – set when unsigned value is out of range  
	– Overflow flag – set when signed value is out of range  
• The MOV instruction never affects the flags.

## Concept Map
![[Pasted image 20231016174533.png]]

## Zero Flag
The Zero flag is set when the result of an operation  
produces zero in the destination operand.

• A flag is set when it equals 1.  
• A flag is clear when it equals 0.  
mov cx,1  
sub cx,1 ; CX = 0, ZF = 1  
mov ax,0FFFFh  
inc ax ; AX = 0, ZF = 1  
inc ax ; AX = 1, ZF = 0

## Sign Flag (SF)
The Sign flag is set when the destination operand is  
negative. The flag is clear when the destination is  
positive.

mov al,0  
sub al,1 ; AL = 11111111b, SF = 1  
add al,2 ; AL = 00000001b, SF = 0  
The sign flag is a copy of the destination's highest  
bit:  
mov cx,0  
sub cx,1 ; CX = -1, SF = 1  
add cx,2 ; CX = 1, SF = 

## Signed and Unsigned Integers  
A Hardware Viewpoint
• All CPU instructions operate exactly the same on  
signed and unsigned integers  
• The CPU cannot distinguish between signed and  
unsigned integers  
• YOU, the programmer, are solely responsible for  
using the correct data type with each instruction

## Overflow and Carry Flags A Hardware  Viewpoint
MSB = Most Significant Bit (high-order bit)  
XOR = eXclusive-OR operation  
NEG = Negate (same as SUB 0,operand )  
• How the ADD instruction affects OF and CF:  
– CF = (carry out of the MSB)  
– OF = CF XOR MSB  
• How the SUB instruction affects OF and CF:  
– CF = INVERT (carry out of the MSB)  
– negate the source and add it to the destination  
– OF = CF XOR MSB  

## Carry Flag (CF)
mov al,0FFh  
add al,1 ; CF = 1, AL = 00  
; Try to go below zero:  
mov al,0  
sub al,1 ; CF = 1, AL = FF  
The Carry flag is set when the result of an operation  
generates an unsigned value that is out of range  
(too big or too small for the destination operand).

## Overflow Flag (OF)
The Overflow flag is set when the signed result of  
an operation is invalid or out of range.
```
; Example 1  
mov al,+127  
add al,1 ; OF = 1, AL = ??  
; Example 2  
mov al,7Fh ; OF = 1, AL = 80h  
add al,1
```
The two examples are identical at the binary level because 7Fh  
equals +127. To determine the value of the destination operand,  
it is often easier to calculate in hexadecimal.

## A Rule of Thumb
When adding two integers, remember that the  
Overflow flag is only set when . . .  
– Two positive operands are added and their sum is  
negative  
– Two negative operands are added and their sum is  
positive

```
mov al,-128  
neg al ; CF = 1 OF = 1  
mov ax,8000h  
add ax,2 ; CF = 0 OF = 0  
mov ax,0  
sub ax,2 ; CF = 1 OF = 0  
mov al,-5  
sub al,+125 ; OF = 1
```

## OFFSET Operator
- OFFSET returns the distance in bytes, of a label  
from the beginning of its enclosing segment  
– Protected mode: 32 bits  
– Real mode: 16 bits

```

.data  
bVal BYTE ?  
wVal WORD ?  
dVal DWORD ?  
dVal2 DWORD ?  
.code  
mov esi,OFFSET bVal ; ESI = 00404000  
mov esi,OFFSET wVal ; ESI = 00404001  
mov esi,OFFSET dVal ; ESI = 00404003  
mov esi,OFFSET dVal2 ; ESI = 00404007  
Let's assume that the data segment begins at  
00404000h:
```

## PTR Operator
Overrides the default type of a label (variable).  
Provides the flexibility to access part of a variable.
```
.data  
myDouble DWORD 12345678h  
.code  
mov ax,myDouble ; error – why?  
mov ax,WORD PTR myDouble ; loads 5678h  
mov WORD PTR myDouble,4321h ; saves 4321h
```

Little endian order is used when storing data in  
memory

## Little Endian Order
• Little endian order refers to the way Intel stores integers  
in memory.  
• Multi-byte integers are stored in reverse order, with the  
least significant byte stored at the lowest address  
• For example, the doubleword 12345678h would be  
stored as:

## PTR Operator Examples

```
mov al,BYTE PTR myDouble ; AL = 78h  
mov al,BYTE PTR [myDouble+1] ; AL = 56h  
mov al,BYTE PTR [myDouble+2] ; AL = 34h  
mov ax,WORD PTR myDouble ; AX = 5678h  
mov ax,WORD PTR [myDouble+2] ; AX = 1234h
```

## TYPE Operator
The TYPE operator returns the size, in bytes, of a  
single element of a data declaration.

```
.data  
var1 BYTE ?  
var2 WORD ?  
var3 DWORD ?  
var4 QWORD ?  
.code  
mov eax,TYPE var1 ; 1  
mov eax,TYPE var2 ; 2  
mov eax,TYPE var3 ; 4  
mov eax,TYPE var4 ; 8
```
## LENGTHOF Operator
The LENGTHOF operator counts the number of  
elements in a single data declaration.
```
.data LENGTHOF  
byte1 BYTE 10,20,30 ; 3  
array1 WORD 30 DUP(?),0,0 ; 32  
array2 WORD 5 DUP(3 DUP(?)) ; 15  
array3 DWORD 1,2,3,4 ; 4  
digitStr BYTE "12345678",0 ; 9  
.code  
mov ecx,LENGTHOF array1 ; 32
```

## SIZEOF Operator
```
.data SIZEOF  
byte1 BYTE 10,20,30 ; 3  
array1 WORD 30 DUP(?),0,0 ; 64  
array2 WORD 5 DUP(3 DUP(?)) ; 30  
array3 DWORD 1,2,3,4 ; 16  
digitStr BYTE "12345678",0 ; 9  
.code  
mov ecx,SIZEOF array1 ; 64  
```

The SIZEOF operator returns a value that is  
equivalent to multiplying LENGTHOF by TYPE.

## Spanning Multiple Lines
A data declaration spans multiple lines if each line  
(except the last) ends with a comma. The  
LENGTHOF and SIZEOF operators include all lines  
belonging to the declaration:

```
.data  
array WORD 10,20,  
30,40,  
50,60  
.code  
mov eax,LENGTHOF array ; 6  
mov ebx,SIZEOF array ; 12
```

In the following example, array identifies only the  
first WORD declaration. Compare the values  
returned by LENGTHOF and SIZEOF here to those  
in the previous slide:

```
.data  
array WORD 10,20  
WORD 30,40  
WORD 50,60  
.code  
mov eax,LENGTHOF array ; 2  
mov ebx,SIZEOF array ; 4
```
## LABEL Directive
• Assigns an alternate label name and type to an  
existing storage location  
• LABEL does not allocate any storage of its own  
• Removes the need for the PTR operator
```

.data  
dwList LABEL DWORD  
wordList LABEL WORD  
intList BYTE 00h,10h,00h,20h  
.code  
mov eax,dwList ; 20001000h  
mov cx,wordList ; 1000h  
mov dl,intList ; 00h  
```

## Indirect Operands
An indirect operand holds the address of a variable,  
usually an array or string. It can be dereferenced  
(just like a pointer).

```
.data  
val1 BYTE 10h,20h,30h  
.code  
mov esi,OFFSET val1  
mov al,[esi] ; dereference ESI (AL = 10h)  
inc esi  
mov al,[esi] ; AL = 20h  
inc esi  
mov al,[esi] ; AL = 30h
```
## Indirect Operands
Use PTR to clarify the size attribute of a memory  
operand.

```
.data  
myCount WORD 0  
.code  
mov esi,OFFSET myCount  
inc [esi] ; error: ambiguous  
inc WORD PTR [esi] ; ok
```

## Array Sum Example
Indirect operands are ideal for traversing an array.  
Note that the register in brackets must be  
incremented by a value that matches the array type.

```
.data  
arrayW WORD 1000h,2000h,3000h  
.code  
mov esi,OFFSET arrayW  
mov ax,[esi]  
add esi,2 ; or: add esi,TYPE arrayW  
add ax,[esi]  
add esi,2  
add ax,[esi] ; AX = sum of the array
```

## Indexed Operands
An indexed operand adds a constant to a register to  
generate an effective address. There are two notational  
forms:

```
.data  
arrayW WORD 1000h,2000h,3000h  
.code  
mov esi,0  
mov ax,[arrayW + esi] ; AX = 1000h  
mov ax,arrayW[esi] ; alternate format  
add esi,2  
add ax,[arrayW + esi]  
etc.  
```
## Index Scaling
You can scale an indirect or indexed operand to the  
offset of an array element. This is done by  
multiplying the index by the array's TYPE:

```
.data  
arrayB BYTE 0,1,2,3,4,5  
arrayW WORD 0,1,2,3,4,5  
arrayD DWORD 0,1,2,3,4,5  
.code  
mov esi,4  
mov al,arrayB[esi*TYPE arrayB] ; 04  
mov bx,arrayW[esi*TYPE arrayW] ; 0004  
mov edx,arrayD[esi*TYPE arrayD] ; 00000004
```

## Pointers
You can declare a pointer variable that contains the  
offset of another variable.

```
.data  
arrayW WORD 1000h,2000h,3000h  
ptrW DWORD arrayW  
.code  
mov esi,ptrW  
mov ax,[esi] ; AX = 1000h
```

## JMP Instruction
• JMP is an unconditional jump to a label that is  
usually within the same procedure.  
• Syntax: JMP target  
• Logic: EIP  target

## LOOP Instruction
The LOOP instruction creates a counting loop  
• Syntax: LOOP target  
• Logic:  
– ECX  ECX – 1  
– if ECX != 0, jump to target  
• Implementation:  
– The assembler calculates the distance, in bytes,  
between the offset of the following instruction and the  
offset of the target label. It is called the relative offset.  
– The relative offset is added to EIP.

## LOOP Example
The following loop calculates the sum of the  
integers 5 + 4 + 3 +2 + 1:

## Nested Loop
If you need to code a loop within a loop, you must save the outer  
loop counter's ECX value. In the following example, the outer loop  
executes 100 times, and the inner loop 20 times.
```

.data  
count DWORD ?  
.code  
mov ecx,100 ; set outer loop count  
L1:  
mov count,ecx ; save outer loop count  
mov ecx,20 ; set inner loop count  
L2: .  
.  
loop L2 ; repeat the inner loop  
mov ecx,count ; restore outer loop count  
loop L1 ; repeat the outer loop  
```

## Summing an Integer Array
The following code calculates the sum of an array of  
16-bit integers.

```
.data  
intarray WORD 100h,200h,300h,400h  
.code  
	mov edi,OFFSET intarray ; address of intarray  
	mov ecx,LENGTHOF intarray ; loop counter  
	mov ax,0 ; zero the accumulator  
L1:  
	add ax,[edi] ; add an integer  
	add edi,TYPE intarray ; point to next integer  
	loop L1 ; repeat until ECX = 0
```

## Copying a String
The following code copies a string from source to  
target:

```
.data  
source BYTE "This is the source string",0  
target BYTE SIZEOF source DUP(0)  
.code  
	mov esi,0 ; index register  
	mov ecx,SIZEOF source ; loop counter  
L1:  
	mov al,source[esi] ; get char from source  
	mov target[esi],al ; store it in the target  
	inc esi ; move to next character  
	loop L1 ; repeat for entire string
```

## 64-Bit Programming
• MOV instruction in 64-bit mode accepts operands  
of 8, 16, 32, or 64 bits  
• When you move a 8, 16, or 32-bit constant to a  
64-bit register, the upper bits of the destination are  
cleared.  
• When you move a memory operand into a 64-bit  
register, the results vary:  
– 32-bit move clears high bits in destination  
– 8-bit or 16-bit move does not affect high bits in  
destination  

MOVSXD sign extends a 32-bit value into a 64-bit  
destination register  
• The OFFSET operator generates a 64-bit address  
• LOOP uses the 64-bit RCX register as a counter  
• RSI and RDI are the most common 64-bit index  
registers for accessing arrays.

• ADD and SUB affect the flags in the same way as  
in 32-bit mode  
• You can use scale factors with indexed operands.
