#### Binary to decimal 
- dec = 2^n-1 + 2^n-2 + ... + 2^1 + 2^0
	- e.g 00001001 = 9
		- (1 x 2^3) + (1 x 2^0) = 9
## Dec to Binary
````
1. Start with the decimal number you want to convert to binary.
2. Divide the number by 2.
3. Write down the quotient (the result of the division) and the remainder.
4. Take the quotient from step 3 and repeat the process, dividing it by 2.
5. Write down the new quotient and remainder.
6. Continue this process until the quotient becomes 0.
7. Your binary representation is the sequence of remainders read from bottom to top.

Let's take an example: Convert the decimal number 27 to binary.

1. 27 ÷ 2 = 13 with a remainder of 1.
2. 13 ÷ 2 = 6 with a remainder of 1.
3. 6 ÷ 2 = 3 with a remainder of 0.
4. 3 ÷ 2 = 1 with a remainder of 1.
5. 1 ÷ 2 = 0 with a remainder of 1.
````

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
## Cache Memory
- High speed expensive static RAM both inside and outside the CPUL
		- Leel-1 Cache: inside the CPU
		-  level-2 Cache: outside the CPU
	- Cache hit: when the data we want o hit is already in cache memory
	- Cache miss: when data to be read is not in cache memory and needs to be brought in
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
## Basics of Assembly

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
## Little Endian Order
• All data types larger than a byte store their  
	individual bytes in reverse order. The least  
	significant byte occurs at the first (lowest) memory  
	address.  
• Example:  
val1 DWORD 12345678h
![[Pasted image 20231015201944.png]]

## Adding Variables to AddSub
````
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

## Calculating the Size of a Byte Array
current location counter: $  
– subtract address of list  
– difference is the number of bytes  
list BYTE 10,20,30,40  
ListSize = ($ - list)

This works for other lists just with more data divide the list
I.e. ListSize = ($ - list) / 2 for Word
I.e. ListSize = ($ - list) / 4 for DoubleWord
etc...

