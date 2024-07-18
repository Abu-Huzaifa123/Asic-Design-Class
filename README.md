# Asic-Design-Class
Task-1

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

Task-2

Compile same code and run it onto RISC-V gcc compiler.

Step:1

Compiled the c code on RISC-V compiler using `cat Sum1tox.c`. 

![Screenshot 2024-07-18 195246](https://github.com/user-attachments/assets/6899beb4-d383-4b27-a502-3cd120e7b846)

Step:2

Then convert the C program to assembly code using `riscv64-unknown-elf-objdump -d sum1tox`
and after that use this command: `riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum1tox Sum1tox.c` to compile the program.

Step:3

Finally we use  `riscv64-unknown-elf-objdump -d sum1tox | less` to dump the assembly code in terminal.

![Screenshot 2024-07-18 192606](https://github.com/user-attachments/assets/94ad7db1-6a88-4d29-9afa-be0ba5166ffe)

Now we can see that our output is same at 1018c location using both gcc and RISCV compiler.


