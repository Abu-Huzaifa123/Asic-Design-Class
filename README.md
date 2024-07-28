# Asic-Design-Class
## Task-1

Write a C code and compile it on gcc compiler.

This repository contains a simple C program that calculates the sum of n numbers.

File: Sum1tox.c
This is the main source file containing the C program.
Compilation: Compiled using gcc
`gcc -o sum1tox Sum1tox.c`

`-o sum1tox`: Specifies the output file name as sum1tox

Sum1tox.c: Input source file name

Execution: After compilation, execute the program with the command `./sum1tox.`


![Screenshot 2024-07-17 092149](https://github.com/user-attachments/assets/af84717b-b0c1-4f8a-9d30-8d80195b5b6d)

## Task-2

Compile same code and run it onto RISC-V gcc compiler.

**Step:1**

Compiled the c code on RISC-V compiler using `cat Sum1tox.c`. 

![Screenshot 2024-07-18 195246](https://github.com/user-attachments/assets/6899beb4-d383-4b27-a502-3cd120e7b846)

**Step:2**

Then convert the C program to assembly code using `riscv64-unknown-elf-objdump -d sum1tox`
and after that use this command: `riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum1tox Sum1tox.c` to compile the program.

**Step:3**

Finally we use  `riscv64-unknown-elf-objdump -d sum1tox | less` to dump the assembly code in terminal.

![Screenshot 2024-07-18 192606](https://github.com/user-attachments/assets/94ad7db1-6a88-4d29-9afa-be0ba5166ffe)

Now we can see that our output is same at 1018c location using both gcc and RISCV compiler.


## Task-3:To find the output of C program on the RISC V Compiler and debug each instruction using the Spike command.

**Step-1:** Firstly we verified that our c code result come from gcc and Risc-V compiler are equal and then we start debugging using `spike -d pk sum1tox` command.

![Screenshot 2024-07-21 142420](https://github.com/user-attachments/assets/d04d0992-002d-437e-98b4-f4af68473c0d)

**Step-2:** The Assembly code of our C program is:

![Screenshot 2024-07-21 104126](https://github.com/user-attachments/assets/832f190c-048a-46c8-91a8-3fc81b4e1869)



**Step-3:** From the assembly code we can see that the first address is at 100b0. To debug it we use the following command: `until pc 0 100b0`
Our first instruction is reg 0. To check it's content we use following code: `reg 0 a0`. Similarly we can get content of each and every line of our assembly code.

![Screenshot 2024-07-21 104507](https://github.com/user-attachments/assets/389df2cf-23ac-42f1-8ee6-cf2b2b22f17a)

## Task-4: To run assembly instructions using a given verilog code for a risc-V processor.

| Operation                | RISC-V ISA  |
|--------------------------|-------------|
| ADD r8, r9, r10          | 00A482B3    |
| SUB r10, r8, r9          | 409482B3    |
| AND r9, r8, r10          | 00A4C2B3    |
| OR r8, r9, r5            | 005482B3    |
| XOR r8, r8, r4           | 004482B3    |
| SLT r00, r1, r4          | 004002B3    |
| ADDI r02, r2, 5          | 00510113    |
| SW r2, r0, 4            | 00412023    |
| SRL r06, r01, r1         | 00119533    |
| BNE r0, r0, 20           | 01400063    |
| BEQ r0, r0, 15           | 00F00063    |
| LW r03, r01, 2           | 00210183    |
| SLL r05, r01, r1         | 00109533    |

