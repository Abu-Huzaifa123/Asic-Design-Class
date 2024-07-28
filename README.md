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


| Operation         | RISC-V ISA      | Hardcoded ISA   | Instruction Format |
|-------------------|-----------------|-----------------|---------------------|
| ADD r8, r9, r10   | 32’h00A482B3    | 32'h02208300    | R-type              |
| SUB r10, r8, r9   | 32’h409482B3    | 32'h02209380    | R-type              |
| AND r9, r8, r10   | 32’h00A4C2B3    | 32'h0230A400    | R-type              |
| OR r8, r9, r5     | 32’h005482B3    | 32'h02513480    | R-type              |
| XOR r8, r8, r4    | 32’h004482B3    | 32'h0240C500    | R-type              |
| SLT r00, r1, r4   | 32’h004002B3    | 32'h02415580    | R-type              |
| ADDI r02, r2, 5   | 32’h00510113    | 32'h00520600    | I-type              |
| SW r2, r0, 4      | 32’h00412023    | 32'h00209181    | S-type              |
| SRL r06, r01, r1  | 32’h00119533    | 32'h00271803    | R-type              |
| BNE r0, r0, 20    | 32’h01400063    | 32'h01409002    | B-type              |
| BEQ r0, r0, 15    | 32’h00F00063    | 32'h00F00002    | B-type              |
| LW r03, r01, 2    | 32’h00210183    | 32'h00208681    | I-type              |
| SLL r05, r01, r1  | 32’h00109533    | 32’h00208783    | R-type              |

The following commands were used to run the verilog code:

![Screenshot 2024-07-28 144818](https://github.com/user-attachments/assets/60344dc3-8cee-4b74-9d50-9fba65bd99e1)

The given hardcoded instructions are:

![Screenshot 2024-07-28 115648](https://github.com/user-attachments/assets/2984cac6-79ba-4429-a171-baa32e2f4117)

Our verilog program instructions are:

![Screenshot 2024-07-28 125110](https://github.com/user-attachments/assets/a5c481a8-89f9-4d21-83bd-02b378466c7e)


Here in this code there are some mismatch in the below images because the code which we are using is already hardcoded:


`ADD R8, R9, R10`

This is the waveform of the given hardcoded verilog program:

![Screenshot 2024-07-28 115909](https://github.com/user-attachments/assets/a25b54d1-dc1d-4d60-8591-835493c83d55)

This is the waveform of our verilog program:

![Screenshot 2024-07-28 140238](https://github.com/user-attachments/assets/b3905a23-b725-4876-af62-8a26068ca64e)


`SUB R10, R8, R9`

This is the waveform of the given hardcoded verilog program:

![Screenshot 2024-07-28 115942](https://github.com/user-attachments/assets/3adb8b54-269f-4fae-a213-16f37cd9f701)

This is the waveform of our verilog program:

![Screenshot 2024-07-28 140315](https://github.com/user-attachments/assets/fbe28a5c-a1d7-471e-a477-2dd75a885a2d)

`AND R9, R8, R10`

 This is the waveform of the given hardcoded verilog program:

 ![Screenshot 2024-07-28 120013](https://github.com/user-attachments/assets/a7426e2c-fc90-4047-ad83-e081414119ec)

 This is the waveform of our verilog program:

 ![Screenshot 2024-07-28 140330](https://github.com/user-attachments/assets/fcbfebaa-0100-4f14-9a92-1c55127a898b)


 `OR R8, R9, R5`

  This is the waveform of the given hardcoded verilog program:

  ![Screenshot 2024-07-28 120035](https://github.com/user-attachments/assets/80f8c2a2-03b9-4c4b-8bd5-49101ffaaad3)

  This is the waveform of our verilog program:

  ![Screenshot 2024-07-28 140347](https://github.com/user-attachments/assets/4f63a635-3a6d-4f5f-909c-483181f553b3)

  `XOR r8, r8, r4`

  This is the waveform of the given hardcoded verilog program:

  ![Screenshot 2024-07-28 120128](https://github.com/user-attachments/assets/de4b3cf8-4eef-4868-b5ef-3d10d976c579)

  This is the waveform of our verilog program:

  ![Screenshot 2024-07-28 140403](https://github.com/user-attachments/assets/aefa8bf4-491e-42f4-a685-09576e3f7ff2)

  `SLT r00, r1, r4 `

  This is the waveform of the given hardcoded verilog program:

  ![Screenshot 2024-07-28 120156](https://github.com/user-attachments/assets/7c3b22f6-db6e-4aaf-9f55-b564e8c6f8ad)

  This is the waveform of our verilog program:

  ![Screenshot 2024-07-28 140426](https://github.com/user-attachments/assets/fa74712f-9fab-4c9b-939b-f091414b9859)

  `ADDI r02, r2, 5 `

  This is the waveform of the given hardcoded verilog program:

  ![Screenshot 2024-07-28 120220](https://github.com/user-attachments/assets/32fefec3-ba90-4f8d-bdd3-c453cdcfc516)

  This is the waveform of our verilog program:

  ![Screenshot 2024-07-28 140442](https://github.com/user-attachments/assets/5c2c48df-ea70-45ef-8f44-6238c33ff02c)

  

  


  

  



  


  




 





