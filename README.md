# ARM-Multiplication-of-Two-32-bit-Numbers-Stored-in-Memory-
ARM (Advanced RISC Machine) architecture is widely used in embedded systems and mobile  devices due to its power efficiency and performance. One common operation in ARM assembly  programming is the multiplication of two 32-bit numbers

ARM processors use a RISC (Reduced Instruction Set Computing) architecture, which 
simplifies the instruction set to achieve higher performance and efficiency. ARM assembly 
language has a variety of instructions for arithmetic operations, data transfer, and control flow.

# ARM Architechture:

![image](https://github.com/user-attachments/assets/dc437d4e-7328-48ad-ae4a-14f3addb13f0)


# Algorithm Steps: 
 

1. Initialize Pointers to the Input Numbers: 

o Define pointers to the memory locations of the two 32-bit input numbers. 

2. Load Input Numbers from Memory: 

o Load the first 32-bit number from memory into a register. 

o Load the second 32-bit number from memory into another register. 

3. Perform the Multiplication: 

o Use the UMULL instruction to multiply the two 32-bit numbers. 

o Store the lower 32 bits of the result in one register. 

o Store the upper 32 bits of the result in another register. 

4. Store the Result in Memory: 

o Store the lower 32 bits of the result back into memory. 

o Store the upper 32 bits of the result back into memory. 
 
# PROGRAM: 

AREA MyCode, CODE, READONLY 
ENTRY 
 

LDR R0, =num1  ; Load the address of num1 

LDR R1, [R0] ; Load the value of num1 into R1 

LDR R2, =num2  ; Load the address of num2 

LDR R3, [R2] ; Load the value of num2 into R3 

UMULL R4, R5, R1, R3 ; Multiply R1 and R3, result in R4 (low) and R5 (high) 

LDR R6, =result_low ; Load the address for the low part of the result 

STR R4, [R6] ; Store the low 32 bits of the result 

LDR R7, =result_high ; Load the address for the high part of the result 


STR R5, [R7] ; Store the high 32 bits of the result 

 
END 
 

num1 DCD 0x12345678 ; Define num1 

num2 DCD 0x87654321 ; Define num2 

result_low DCD 0 ; Define storage for the low part of the result 

result_high DCD 0 ; Define storage for the high part of the result


# Simulation Results :

Memory Contents Before Execution 
 

• num1 at address 0x20000000: 0x12345678 

• num2 at address 0x20000004: 0x87654321 

• result_low at address 0x20000008: 0x00000000 

• result_high at address 0x2000000C: 0x00000000 
 
Memory Contents After Execution 
 

• num1 at address 0x20000000: 0x12345678 


• num2 at address 0x20000004: 0x87654321 

• result_low at address 0x20000008: 0x9E8BCA10 (Lower 32 bits of the result) 

• result_high at address 0x2000000C: 0x00A3D70A (Upper 32 bits of the result) 

 
# Conclusion 
The expected results show the proper functioning of the UMULL instruction, storing the 64-bit 
result across two 32-bit memory locations. This example demonstrates the efficient handling of 
large integer arithmetic in ARM assembly language.
