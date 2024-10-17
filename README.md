# Asic-Design-Class
<details>
 
<summary> <h2>Task-1</h2> </summary>

## Task-1: Write a C code and compile it on gcc compiler.

This repository contains a simple C program that calculates the sum of n numbers.

File: Sum1tox.c
This is the main source file containing the C program.
Compilation: Compiled using gcc
`gcc -o sum1tox Sum1tox.c`

`-o sum1tox`: Specifies the output file name as sum1tox

Sum1tox.c: Input source file name

Execution: After compilation, execute the program with the command `./sum1tox.`


![Screenshot 2024-07-17 092149](https://github.com/user-attachments/assets/af84717b-b0c1-4f8a-9d30-8d80195b5b6d)




## Compile same code and run it onto RISC-V gcc compiler.

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

</details>

<details>
 
<summary> <h2>Task-2</h2> </summary>

## Task-2:To find the output of C program on the RISC V Compiler and debug each instruction using the Spike command.

**Step-1:** Firstly we verified that our c code result come from gcc and Risc-V compiler are equal and then we start debugging using `spike -d pk sum1tox` command.

![Screenshot 2024-07-21 142420](https://github.com/user-attachments/assets/d04d0992-002d-437e-98b4-f4af68473c0d)

**Step-2:** The Assembly code of our C program is:

![Screenshot 2024-07-21 104126](https://github.com/user-attachments/assets/832f190c-048a-46c8-91a8-3fc81b4e1869)



**Step-3:** From the assembly code we can see that the first address is at 100b0. To debug it we use the following command: `until pc 0 100b0`
Our first instruction is reg 0. To check it's content we use following code: `reg 0 a0`. Similarly we can get content of each and every line of our assembly code.

![Screenshot 2024-07-21 104507](https://github.com/user-attachments/assets/389df2cf-23ac-42f1-8ee6-cf2b2b22f17a)

</details>
 
<details>
 
<summary> <h2>Task-3</h2> </summary>

## Task-3: To run assembly instructions using a given verilog code for a risc-V processor.


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

  `SW r2, r0, 4`

   This is the waveform of the given hardcoded verilog program:

   ![Screenshot 2024-07-28 120245](https://github.com/user-attachments/assets/71704811-25de-4352-a6b1-8472d0988329)

   This is the waveform of our verilog program:

   ![Screenshot 2024-07-28 140458](https://github.com/user-attachments/assets/5965733c-a2c4-435b-90a3-47caa206a3c7)

   `SRL r06, r01, r1`

   This is the waveform of our verilog program:

   ![Screenshot 2024-07-28 140514](https://github.com/user-attachments/assets/ef1666db-b95a-4452-b19d-763d206200fd)

   `BNE r0, r0, 20`

   This is the waveform of our verilog program:

   ![Screenshot 2024-07-28 184617](https://github.com/user-attachments/assets/69ce370e-a8cd-4f9e-b309-208f7ef74fed)

   `BEQ r0, r0, 15`

   This is the waveform of our verilog program:

   ![Screenshot 2024-07-28 184650](https://github.com/user-attachments/assets/0f774abb-2bb4-4771-8733-9a26d3261b87)

</details>
 

<details>
 
<summary> <h2>Task-4</h2> </summary>

## Task:4-->> To write an Application in C, compile it with gcc and Risc-v gcc
**Application:To design a Voting Machine which takes input from users and give final result according to inputs.** 

**Step:1-->> C code of the application**

> code

``` c
#include<stdio.h> 

int main() { 
    char n[10]; 
    int a[10], csp = 0, bjp = 0, bsp = 0, sp = 0, nota = 0, win = 0;

    again: 
    printf("\nPlease enter your name:"); 
    scanf("%s", n);

    printf("\nHello %s please enter your age:", n); 
    scanf("%d", &a[0]); // a[0] for age.

    if(a[0] >= 18) { 
        printf("\nYou are eligible for voting!\nLet's start the process."); 
        printf("\nEnter 1-CONGRESS\nEnter 2-BJP\nEnter 3-BAHUJAN SAMAJWADI PARTY\nEnter 4-SAMAJWADI PARTY\nEnter 5-NOTA\n:"); 
        scanf("%d", &a[1]); // a[1] for your vote.

        if(a[1] == 1) csp++; 
        if(a[1] == 2) bjp++; 
        if(a[1] == 3) bsp++; 
        if(a[1] == 4) sp++; 
        if(a[1] == 5) nota++;

        printf("\nAll process is completed! Here is your receipt."); 
        printf("\nReceipt:\nName: %s\nAge: %d", n, a[0]);

        if(a[1] == 1) printf("\nVote: CONGRESS"); 
        if(a[1] == 2) printf("\nVote: BJP"); 
        if(a[1] == 3) printf("\nVote: BAHUJAN SAMAJWADI PARTY"); 
        if(a[1] == 4) printf("\nVote: SAMAJWADI PARTY"); 
        if(a[1] == 5) printf("\nVote: NOTA");

        printf("\nThanks for visiting :)");

        nefv: 
        printf("\nEnter 0 for exit\nEnter 1 for allowing another person to vote:"); 
        scanf("%d", &a[2]);

        if(a[2] == 0) { 
            printf("\nResult of voting\nCONGRESS = %d\nBJP = %d\nBAHUJAN SAMAJWADI PARTY = %d\nSAMAJWADI PARTY = %d\nNOTA = %d", csp, bjp, bsp, sp, nota);
            win = ((csp > bjp) && (csp > bsp) && (csp > sp)) ? csp :
                  ((bjp > csp) && (bjp > bsp) && (bjp > sp)) ? bjp :
                  ((bsp > bjp) && (bsp > csp) && (bsp > sp)) ? bsp :
                  ((sp > bjp) && (sp > csp) && (sp > bsp)) ? sp : nota;

            if(win == bjp) printf("\nThe Winner is BJP!"); 
            if(win == csp) printf("\nThe Winner is CONGRESS!"); 
            if(win == bsp) printf("\nThe Winner is BAHUJAN SAMAJWADI PARTY!"); 
            if(win == sp) printf("\nThe Winner is SAMAJWADI PARTY!"); 
            if((win == nota) && (bjp == 0) && (csp == 0) && (bsp == 0) && (sp == 0)) 
                printf("\nNo one got any votes, that's why voting is postponed and voting dates will be available soon!"); 
            if(win < nota) printf(", but NOTA got more votes than the winner.");
        } 
        
        if(a[2] == 1) 
            goto again; 
    } else { 
        printf("\nYou are not eligible for voting.\nThanks for visiting!"); 
        goto nefv; 
    } // Not eligible for voting.

    return 0; 
}
```

**Step:2-->> Compilation using gcc compiler: For this we used command `gcc -o Asic_Application Application.c`**

file:///home/vsduser/Pictures/Screenshot%20from%202024-08-14%2018-37-17.png![image](https://github.com/user-attachments/assets/d8b7ada4-b82c-4cea-b70c-563c66c6be24)



**Step:3-->> Compilation using risc-v by O1 with `riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o Asic_Application Application.c` command**


``` c
vsduser@vsduser-VirtualBox:~/Downloads$ riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o Asic_Application Application.c 
vsduser@vsduser-VirtualBox:~/Downloads$ gcc Application.c 
vsduser@vsduser-VirtualBox:~/Downloads$ ./a.out

Please enter your name:Huzaifa

Hello Huzaifa please enter your age:23

You are eligible for voting!
Let's start the process.
Enter 1-CONGRESS
Enter 2-BJP
Enter 3-BAHUJAN SAMAJWADI PARTY
Enter 4-SAMAJWADI PARTY
Enter 5-NOTA
:5

All process is completed! Here is your receipt.
Receipt:
Name: Huzaifa
Age: 23
Vote: NOTA
Thanks for visiting :)
Enter 0 for exit
Enter 1 for allowing another person to vote:0

Result of voting
CONGRESS = 0
BJP = 0
BAHUJAN SAMAJWADI PARTY = 0
SAMAJWADI PARTY = 0
NOTA = 1
No one got any votes, that's why voting is postponed and voting dates will be available soon!
```

**Step:4-->> To debug each instruction using the O1 by `spike pk` command**

``` c
vsduser@vsduser-VirtualBox:~/Downloads$ riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o Asic_Application
vsduser@vsduser-VirtualBox:~/Downloads$ spike pk Asic_Application 
bbl loader

Please enter your name:Huzaifa

Hello Huzaifa please enter your age:23

You are eligible for voting!
Let's start the process.
Enter 1-CONGRESS
Enter 2-BJP
Enter 3-BAHUJAN SAMAJWADI PARTY
Enter 4-SAMAJWADI PARTY
Enter 5-NOTA
:5

All process is completed! Here is your receipt.
Receipt:
Name: Huzaifa
Age: 23
Vote: NOTA
Thanks for visiting :)
Enter 0 for exit
Enter 1 for allowing another person to vote:0

Result of voting
CONGRESS = 0
BJP = 0
BAHUJAN SAMAJWADI PARTY = 0
SAMAJWADI PARTY = 0
NOTA = 1
No one got any votes, that's why voting is postponed and voting dates will be available soon!

```

**We can see that output coming from gcc compilation, Risc-v compilation and after debugging by O1 using Spike command is same** 


**Step:5-->> Finally we use `riscv64-unknown-elf-objdump -d Asic_Application | less` to dump the assembly code in terminal.**

file:///home/vsduser/Pictures/Screenshot%20from%202024-08-14%2017-49-09.png![image](https://github.com/user-attachments/assets/c3f72645-4142-4bae-ae0f-0738cf214b18)

</details>

<details>
 
<summary> <h2>Task-5</h2> </summary>

## Task:5-->> To make a Risc-V processor core using TL-Verilog.

TL-Verilog (Transaction-Level Verilog) is an advanced hardware description language that builds upon traditional Verilog, aimed at enhancing productivity and abstraction in digital design. It's particularly suited for complex digital systems, such as processors, where managing and optimizing the design process can be challenging.

Key Concepts of TL-Verilog:

**Transaction-Level Abstraction:**

TL-Verilog focuses on modeling the movement of data at a higher level of abstraction, known as transaction-level modeling. Unlike traditional Verilog, which often emphasizes individual signals and their timing, TL-Verilog deals with transactions—units of data movement between different parts of a digital system. This abstraction simplifies design by allowing engineers to think about the overall data flow rather than individual signal toggles.

**Pipeline Constructs:**

One of the major innovations in TL-Verilog is its approach to pipelining. Pipelines are fundamental in digital systems, particularly in CPUs and other processors, where multiple instructions or operations are processed in parallel. In TL-Verilog, pipelines are explicitly defined and managed, making it easier to visualize, implement, and optimize complex pipelines, reducing the chances of errors that might occur with manual pipeline management in traditional Verilog.

**Implicit Register Management:**

In traditional Verilog, designers must explicitly declare and manage registers—storage elements that hold data. TL-Verilog, however, introduces the concept of implicit registers, where the language automatically handles register allocation based on the designer’s high-level description. This reduces the amount of code that needs to be written and makes the design cleaner and easier to understand.

**Cleaner and Simplified Syntax:**

TL-Verilog offers a more streamlined syntax compared to traditional Verilog, which can be verbose and prone to errors. This simplification not only makes the code easier to write and read but also helps in reducing bugs and speeding up the overall development process.

**Scalability:**

The language is designed with scalability in mind. As digital designs grow in complexity, managing them in traditional Verilog can become increasingly difficult. TL-Verilog’s higher-level constructs and abstractions allow for more efficient management of large-scale designs, making it easier to scale up projects.

**Compatibility with Verilog:**

TL-Verilog is fully compatible with traditional Verilog. This means that designers can integrate TL-Verilog into their existing Verilog-based workflows without needing to completely overhaul their current design processes. This compatibility also allows for gradual adoption, where designers can start using TL-Verilog in parts of their design while still relying on traditional Verilog where necessary.

## Risc-V Architecture:

![Screenshot 2024-08-21 121029](https://github.com/user-attachments/assets/143cee21-5214-4f33-a7dc-cb82efe8ff0e)

> Code
``` c

\m4_TLV_version 1d: tl-x.org
\SV
   // This code can be found in: https://github.com/stevehoover/RISC-V_MYTH_Workshop
   
   m4_include_lib(['https://raw.githubusercontent.com/BalaDhinesh/RISC-V_MYTH_Workshop/master/tlv_lib/risc-v_shell_lib.tlv'])

\SV
   m4_makerchip_module   // (Expanded in Nav-TLV pane.)
\TLV

   // /====================\
   // | Sum 1 to 9 Program |
   // \====================/
   //
   // Program for MYTH Workshop to test RV32I
   // Add 1,2,3,...,9 (in that order).
   //
   // Regs:
   //  r10 (a0): In: 0, Out: final sum
   //  r12 (a2): 10
   //  r13 (a3): 1..10
   //  r14 (a4): Sum
   // 
   // External to function:
   m4_asm(ADD, r10, r0, r0)             // Initialize r10 (a0) to 0.
   // Function:
   m4_asm(ADD, r14, r10, r0)            // Initialize sum register a4 with 0x0
   m4_asm(ADDI, r12, r10, 1010)         // Store count of 10 in register a2.
   m4_asm(ADD, r13, r10, r0)            // Initialize intermediate sum register a3 with 0
   // Loop:
   m4_asm(ADD, r14, r13, r14)           // Incremental addition
   m4_asm(ADDI, r13, r13, 1)            // Increment intermediate register by 1
   m4_asm(BLT, r13, r12, 1111111111000) // If a3 is less than a2, branch to label named <loop>
   m4_asm(ADD, r10, r14, r0)            // Store final result to register a0 so that it can be read by main program
   
   m4_asm(SW, r0, r10, 100)             //Command to check for Load instruction
   m4_asm(LW, r15, r0, 100)             // Command to check for the Store Instruction
   
   
   // Optional:
   // m4_asm(JAL, r7, 00000000000000000000) // Done. Jump to itself (infinite loop). (Up to 20-bit signed immediate plus implicit 0 bit (unlike JALR) provides byte address; last immediate bit should also be 0)
   m4_define_hier(['M4_IMEM'], M4_NUM_INSTRS)

   |cpu
      @0
         $reset = *reset;
         $clk_Abu = *clk;



      // YOUR CODE HERE
      @0
         $pc[31:0] = >>1$reset ? 0 
                    : >>3$valid_taken_br ? >>3$br_target_pc
                    : >>3$valid_load ? >>3$pc_inc
                    : >>1$pc_inc;
         
         $start = !$reset && >>1$reset;
     
         
      @1
         $pc_inc[31:0] = $pc + 32'd4;
         //Fetch logic
         
         $imem_rd_addr[M4_IMEM_INDEX_CNT -1 : 0] = $pc[M4_IMEM_INDEX_CNT +1 : 2];
         $imem_rd_en = !$reset;
         $instr[31:0] = $imem_rd_data[31:0];
         
         // Instruction type 

         $is_i_instr = $instr[6:2] ==? 5'b0000x ||
                       $instr[6:2] ==? 5'b001x0 ||
                       $instr[6:2] ==? 5'b11100 ;

         $is_r_instr = $instr[6:2] ==? 5'b01011 ||
                       $instr[6:2] ==? 5'b01100 ||
                       $instr[6:2] ==? 5'b01110 ||
                       $instr[6:2] ==? 5'b10100 ;
         
         $is_u_instr = $instr[6:2] ==? 5'b0x101;
     
         $is_j_instr = $instr[6:2] ==? 5'b11011;

         $is_b_instr = $instr[6:2] ==? 5'b11000;
         
         $is_s_instr = $instr[6:2] ==? 5'b0100x;
         
                  
         
         
         //decode logic for immediate values
         
         $imm[31:0] = $is_i_instr ? { {21{$instr[31]}}, $instr[30:20]}:
                      $is_s_instr ? { {21{$instr[31]}}, $instr[30:25], $instr[11:7]} :
                      $is_b_instr ? { {20{$instr[31]}}, $instr[7], $instr[30:25], $instr[11:8], 1'b0} :
                      $is_u_instr ? {$instr[31:12], 12'b0} :
                      $is_j_instr ? { {12{$instr[31]}}, $instr[19:12], $instr[20], $instr[30:21], 1'b0} :
                      32'b0;         
                
         //decoding other instruction elements
         
         $opcode[6:0] = $instr[6:0] ;
         
         $rd_valid = $is_r_instr || $is_j_instr || $is_i_instr || $is_u_instr;
         $rs2_valid = $is_r_instr || $is_s_instr || $is_b_instr;
         $rs1_valid = $is_r_instr || $is_i_instr || $is_b_instr || $is_s_instr;
         $funct3_valid = $is_r_instr || $is_i_instr || $is_b_instr || $is_s_instr;
         $funct7_valid = $is_r_instr;
         
         ?$rd_valid
            $rd[4:0] = $instr[11:7];
         
         ?$rs2_valid
            $rs2[4:0] = $instr[24:20];
         ?$rs1_valid
            $rs1[4:0] = $instr[19:15];
         ?$funct3_valid
            $funct3[2:0] = $instr[14:12];
         ?$funct7_valid
            $funct7[6:0] = $instr[31:25];
            
         //decoding instructions

         $dec_bits[10:0] = {$funct7[5],$funct3,$opcode};

         //ADD Instructions 
         $is_addi = $dec_bits ==? 11'bx_000_0010011;
         $is_add  = $dec_bits ==? 11'b0_000_0110011;

         //Subtract Instructions
         $is_sltiu  = $dec_bits ==? 11'bx_011_0010011;
         $is_xori   = $dec_bits ==? 11'bx_100_0010011;
         $is_ori    = $dec_bits ==? 11'bx_110_0010011;
         $is_andi   = $dec_bits ==? 11'bx_111_0010011;
         $is_slli   = $dec_bits ==? 11'b0_001_0010011;
         $is_srli   = $dec_bits ==? 11'b0_101_0010011;
         $is_sral   = $dec_bits ==? 11'b1_101_0010011;
         $is_sub    = $dec_bits ==? 11'b1_000_0110011;
         $is_sll    = $dec_bits ==? 11'b0_001_0110011;
         $is_slt    = $dec_bits ==? 11'b0_010_0110011;
         $is_sltu   = $dec_bits ==? 11'b0_011_0110011;
         $is_xor    = $dec_bits ==? 11'b0_100_0110011;
         $is_srl    = $dec_bits ==? 11'b0_101_0110011;
         $is_sra    = $dec_bits ==? 11'b1_101_0110011;
         $is_or     = $dec_bits ==? 11'b0_110_0110011;
         $is_and    = $dec_bits ==? 11'b0_111_0110011;
         
         //Branch Instructions 
         //BEQ - Branch on equal 
         $is_beq = $dec_bits ==? 11'bx_000_1100011;
         //BNE - Branch not equal
         $is_bne = $dec_bits ==? 11'bx_001_1100011;
         //BLT - Branch on less than
         $is_blt = $dec_bits ==? 11'bx_100_1100011;
         //BGE - Branch on greater than
         $is_bge = $dec_bits ==? 11'bx_101_1100011;
         //BLTU - Branch on less than equal
         $is_bltu = $dec_bits ==? 11'bx_110_1100011;
         //BGEU - Branch on greater than equal
         $is_bgeu = $dec_bits ==? 11'bx_111_1100011;
         
         //LOAD INSTRUCTION
         $is_load   = $dec_bits ==? 11'bx_010_0000011;

         //Miscellaneous Instructions 
         $is_lui    = $dec_bits ==? 11'bx_xxx_0110111;
         $is_auipc  = $dec_bits ==? 11'bx_xxx_0010111;
         $is_jal    = $dec_bits ==? 11'bx_xxx_1101111;
         $is_jalb   = $dec_bits ==? 11'bx_000_1100111;
         $is_sb     = $dec_bits ==? 11'bx_000_0100011;
         $is_sh     = $dec_bits ==? 11'bx_001_0100011;
         $is_sw     = $dec_bits ==? 11'bx_010_0100011;
         $is_slti   = $dec_bits ==? 11'bx_010_0010011;

         
                  
      @2
         
         
         $rf_rd_en1 = $rs1_valid;
         $rf_rd_index1[4:0] = $rs1;
         
         $rf_rd_en2 = $rs2_valid;
         $rf_rd_index2[4:0] = $rs2;
         
         //operating on the read values
         
         $src1_value[31:0] = (>>1$rf_wr_index == $rf_rd_index1) && >>1$rf_wr_en
                             ? >>1$result :
                             $rf_rd_data1;
          
         $src2_value[31:0] = (>>1$rf_wr_index == $rf_rd_index2) && >>1$rf_wr_en
                             ? >>1$result :
                             $rf_rd_data2;
         
         $taken_br = $is_beq ? ($src1_value == $src2_value) :
                     $is_bne ?($src1_value != $src2_value) :
                     $is_bltu ? ($src1_value <  $src2_value) :
                     $is_bgeu ? ($src1_value >= $src2_value) :
                     $is_blt ? (($src1_value < $src2_value) ^ ($src1_value[31] != $src2_value[31])) :
                     $is_bgeu ? (($src1_value >= $src2_value) ^ ($src1_value[31] != $src2_value[31])) :
                            1'b0;
         
         
         $br_target_pc[31:0] = $taken_br? $pc + $imm : 0;
         
         
         
      @3
         
         

         $result[31:0] = $is_add ?
                         $src1_value[31:0] + $src2_value[31:0] :
                         $is_sub ?
                         $src1_value[31:0] - $src2_value[31:0] :
                         $is_and ?
                         $src1_value[31:0] & $src2_value[31:0] :
                         $is_or ?
                         $src1_value[31:0] | $src2_value[31:0] :
                         $is_xor ?
                         $src1_value[31:0] ^ $src2_value[31:0] :
                         $is_addi ? 
                         $src1_value[31:0] + $imm[31:0] :
                         $is_andi ?
                         $src1_value[31:0] & $imm[31:0] :
                         $is_ori ?
                         $src1_value[31:0] | $imm[31:0] :
                         $is_xori ?
                         $src1_value[31:0] ^ $imm[31:0] :

                         //Load and store 
                         $is_load ?
                         $src1_value[31:0] + $imm[31:0] :
                         $is_s_instr ?
                         $src1_value[31:0] + $imm[31:0] :

                         //ALU for some shift operations
                         $is_slli ?
                         $src1_value[31:0] << $imm[5:0] :
                         $is_srli ?
                         $src1_value[31:0] >> $imm[5:0] :
                         $is_sll ?
                         $src1_value[31:0] << $src2_value[4:0] :
                         $is_srl ?
                         $src1_value[31:0] >> $src2_value[4:0] :

                         //ALU for some other operations
                         $is_sltu ? $sltu_rslt :
                         $is_sltiu ? $sltiu_rslt :
                         $is_lui ?
                         {$imm[31:12], 12'b0} :
                         $is_auipc ?
                         $pc + $imm :
                         $is_jal ?
                         $pc + 32'd4 :
                         $is_jalr ?
                         $pc + 32'd4 :
                         $is_srai ?
                         { {32{$src1_value[31]}}, $src1_value} >> $imm[4:0] :
                         $is_slt ?
                         ($src1_value[31] == $src2_value[31]) ? $sltu_rslt : {31'b0, $src1_value[31]} :
                         $is_slti ?
                         ($src1_value[31] == $imm[31]) ? $sltu_rslt : {31'b0, $src1_value[31]} :
                         $is_sra ?
                         { {32{$src1_value[31]}}, $src1_value} >> $src2_value[4:0] :
                         32'bx;
         
         $sltu_rslt[31:0]  = $src1_value[31:0] < $src2_value[31:0];
         $sltiu_rslt[31:0] = $src1_value[31:0] < $imm;
         
         //writing ALU result into register file
         $rf_wr_en = ($rd_valid && $rd!=0 && $valid) || >>2$valid_load ;  //writing only when rd is valid and rd is not equal to x0 register
         $rf_wr_index[4:0] = >>2$valid_load ? >>2$rd : $rd;
         
         $rf_wr_data[31:0] = >>2$valid_load ? >>2$ld_data[31:0] : $result;

         
         //To check branch condition
         
       
         $valid = !((>>1$valid_taken_br) || (>>2$valid_taken_br) || (>>1$valid_load) || (>>2$valid_load));
         
         $valid_taken_br = $valid && $taken_br;
         
         
         $valid_load = $valid && $is_load;
      
      @4
         //Data to memory interface
         $dmem_rd_en = $is_load;
         $dmem_wr_en = $is_s_instr && $valid;
         
         $dmem_addr[3:0] = $result[5:2];
         $dmem_wr_data[31:0] = $src2_value;
           
      @5
         $ld_data[31:0] = $dmem_rd_data;
         
         
         
         
         
            
         
         // Testbench
         *passed = |cpu/xreg[15]>>5$value == (1+2+3+4+5+6+7+8+9);
         
         
                                    
         
  

      // Note: Because of the magic we are using for visualisation, if visualisation is enabled below,
      //       be sure to avoid having unassigned signals (which you might be using for random inputs)
      //       other than those specifically expected in the labs. You'll get strange errors for these.

   
   // Assert these to end simulation (before Makerchip cycle limit).
   *passed = *cyc_cnt > 40;
   *failed = 1'b0;
   
   // Macro instantiations for:
   //  o instruction memory
   //  o register file
   //  o data memory
   //  o CPU visualization
   |cpu
      m4+imem(@1)    // Args: (read stage)
      m4+rf(@2, @3)  // Args: (read stage, write stage) - if equal, no register bypass is required
      m4+dmem(@4)    // Args: (read/write stage)

   m4+cpu_viz(@4)    // For visualisation, argument should be at least equal to the last stage of CPU logic. @4 would work for all labs.
\SV
   endmodule

```

**Generated Diagram from the makerchip of the above code is as shown below:**

![Screenshot 2024-08-21 133937](https://github.com/user-attachments/assets/33a30061-1f7b-4e79-a95b-6e9598cac133)


> Viz


![Screenshot 2024-08-21 134026](https://github.com/user-attachments/assets/5992d910-2d47-4bf0-9f70-8d44808b2919)


> Simulation Output


![Screenshot 2024-08-21 134331](https://github.com/user-attachments/assets/5c618912-b854-41e1-ac75-49545ab4d80a)


**The waveforms generated including my clock name $clk_Abu is shown below:**


![Screenshot 2024-08-21 133809](https://github.com/user-attachments/assets/4be5000f-c5cb-40aa-b97b-cd7626e67139)


**The waveform for the `/xreg[14]` where the sum of this program is store:**


![Screenshot 2024-08-21 133854](https://github.com/user-attachments/assets/87f0d3bb-dbbc-4367-a154-5e004c76cf8f)

</details>
 
<details>
 
<summary> <h2>Task-6</h2> </summary>

## Task:6-->> To convert the TL Verilog code to verilog code using Sandpiper and then use GTKWave for pre-synthesis simulation to verify the design.

**Step:1-->> Install Required Packages:**
``` c

python3-pip git iverilog gtkwave

cd ~

sudo apt-get install python3-venv

python3 -m venv .venv

source ~/.venv/bin/activate

pip3 install pyyaml click sandpiper-saas

```

![Screenshot 2024-08-26 170747](https://github.com/user-attachments/assets/db66297b-4faa-4412-98df-d8887d541b3c)

**Step:2-->> Clone this repo containing VSDBabySoC design files and testbench by command  `git clone https://github.com/manili/VSDBabySoC.git`.**

**Step:3-->> Replace the rvmyth.tlv file in the VSDBabySoC directory to src/module with the rvmth.tlv using command `cd /home/subhasis/VSDBabySoC`.**

![Screenshot 2024-08-26 171241](https://github.com/user-attachments/assets/be677722-d34f-457d-bbd1-0b22f6861849)

**Step:4-->> Convert .tlv to .v using this converter command `sandpiper-saas -i ./src/module/*.tlv -o rvmyth.v --bestsv --noline -p verilog --outdir ./src/module/`**

**Generated Verilog code with clk_Abu is as shown below:**

![Screenshot 2024-08-26 173556](https://github.com/user-attachments/assets/0aaf57ca-cef1-4816-934b-005c72796a90)

**Step:5-->> Make the pre_synth_sim.vcd using command `make pre_synth_sim`**

**Step:6-->> To compile and simulate RISC-V design run the following code `iverilog -o output/pre_synth_sim.out -DPRE_SYNTH_SIM src/module/testbench.v -I src/include -I src/module`**

**Step:7-->> To open the Simulation file in gtkwave tool use the following command `gtkwave pre_synth_sim.vcd`**


![Screenshot 2024-08-26 175726](https://github.com/user-attachments/assets/a030945e-954b-45c2-9ebb-62018d5e5819)

**The below diagram contains my clk signal `clk_Abu` , `reset` signal and `Out[9:0]` of Risc-v Core.**

![Screenshot 2024-08-26 173640](https://github.com/user-attachments/assets/e79b02e4-fb1a-4688-9730-d948bb8254ff)


</details>   

   
    
<details>
 
<summary> <h2>Task-7</h2> </summary>

## Task-7: To convert a digital output from a Verilog file into an analog signal using a DAC and PLL for Risc-V processor. 
    
**The following commands were used to run out Risc-V core inside the BabySoc:**
```c
$ sudo apt-get update
$ git clone https://github.com/YosysHQ/yosys.git
$ cd yosys
$ sudo apt install make (If make is not installed please install it) 
$ sudo apt-get install build-essential clang bison flex \
    libreadline-dev gawk tcl-dev libffi-dev git \
    graphviz xdot pkg-config python3 libboost-system-dev \
    libboost-python-dev libboost-filesystem-dev zlib1g-dev
$ make config-gcc
$ make 
$ sudo make install


```

**Use these commands to install iverilog:**

```c

sudo apt-get update
sudo apt-get install iverilog


```

 **Use these commands to install Gtkwave:**

```c

sudo apt-get update
sudo apt install gtkwave

```

**After that to clone the BabySoc use this command `git clone https://github.com/Subhasis-Sahu/BabySoC_Simulation/`**

**In final step for functional verification we use these commands:**

```c

cd BabySoC_Simulation
iverilog -o ./pre_synth_sim.out -DPRE_SYNTH_SIM src/module/testbench.v -I src/include -I src/module/
./pre_synth_sim.out
gtkwave pre_synth_sim.vcd

```

**These are the snapshots of my terminal window:**

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-09-02%2023-00-10.png![image](https://github.com/user-attachments/assets/9ad567eb-4cb1-40c9-b0df-5a54c781759a)


file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-09-02%2023-01-25.png![image](https://github.com/user-attachments/assets/cff605fe-a0fd-4fff-bcd3-887f2ad705de)

**Below is the output waveforms: We can clearly observe that VCO_IN is the input clk for the PLL and CLK is the clk output from the PLL. clk_Abu is the clock used inside the Risc-V core and OUT is the analog signal coming out of the DAC unit.**


file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-09-02%2022-58-24.png![image](https://github.com/user-attachments/assets/4db83136-2bcd-436a-ba91-6a3413e128a9)


file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-09-02%2022-58-48.png![image](https://github.com/user-attachments/assets/c8972622-fc91-43cc-8282-5b6e5482d885)


 </details>


  <details>
 
<summary> <h2>Task-8</h2> </summary>

## Task-8: Verilog RTL Design and Synthesis.

## Day-1:

### Lab-1: Installation of the files and Repository

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-17%2019-08-13.png![image](https://github.com/user-attachments/assets/6fc3ebcb-8251-4d8d-bf65-1ecc111dce86)


file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-17%2019-12-23.png![image](https://github.com/user-attachments/assets/ef6137a2-6ecd-4b62-a353-af32339d6195)


## Lab-2: Simulation by iverilog and Gtkwave

**In this lab we have implemented the 2*1 mux using it's verilog code and test bench which is already present in the file that we have clone from the github in lab-1**

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-17%2019-29-00.png![image](https://github.com/user-attachments/assets/f5817a28-e5bf-49a9-95a1-fb8916ff4c16)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-17%2019-31-24.png![image](https://github.com/user-attachments/assets/7355f574-1d3e-4df3-a0f7-f23e3c492c5d)

**We can see the verilog code and test bench by this command**

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-17%2019-46-35.png![image](https://github.com/user-attachments/assets/3af042d9-423b-4fcc-a83c-bcfdb4c190e3)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-17%2019-46-16.png![image](https://github.com/user-attachments/assets/28cf989a-8e62-4f5b-8866-200f9c54ca9a)

## Synthesizer:

**A synthesizer is a crucial tool in the digital design process, responsible for converting RTL (Register Transfer Level) code into a gate-level netlist. The netlist is a detailed representation of the circuit, consisting of logical gates and their connections, ready for physical design stages like place and route. In this flow, Yosys is the synthesizer tool being used, which is an open-source framework for Verilog HDL synthesis. Yosys performs various optimization techniques to produce an efficient gate-level implementation from the RTL code.**

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-17%2019-57-47.png![image](https://github.com/user-attachments/assets/419fada9-c527-431e-89e5-6ee0208bd62c)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-17%2019-58-22.png![image](https://github.com/user-attachments/assets/fab22c0d-9c48-4995-9477-d8f358370245)


## Logic Synthesis:

**So, we have an RTL code that describes the design in terms of data flow and operations. To turn this into an actual circuit, we use a process called synthesis. During synthesis, the RTL code is translated into basic logic gates like AND, OR, and NOT, and the connections between these gates are established. This final representation is called a netlist, which defines the structure of the circuit at the gate level.**

**We need synthesis because RTL is more abstract and easier for humans to write and understand, but we need something that can be physically built on a chip. The netlist generated after synthesis can then be used for place and route, where the gates are laid out on a chip and connected. After synthesis, tools can check if the design meets timing requirements, area constraints, and power limits. Without synthesis, we wouldn’t be able to move from high-level design to an actual, manufacturable circuit.**

## Why we need faster cells?

**The combinational delay limits the maximum speed of a digital logic circuit. To minimize this delay, faster cells are needed so the logic can be computed quickly. This ensures that the required logic is generated before the next clock cycle arrives, allowing the circuit to operate efficiently at higher speeds. So we need a setup time for this:**

## Setup Time:

**Setup time is the minimum amount of time before the clock edge during which the input signal (data) to a flip-flop or latch must remain stable. If the data changes within this period, the flip-flop might not capture the correct value, leading to timing violations. Essentially, the data needs to be ready and stable for a certain time before the clock triggers the flip-flop.**

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-17%2020-24-18.png![image](https://github.com/user-attachments/assets/efe113f7-2ae2-4265-b85b-37a9d85496f6)

## Why we need slower cells?

**Slow cells are needed to prevent hold time violations, ensuring the logic is captured correctly after the clock edge. The logic must remain stable for a certain time (hold time), and if faster gates are used, it can lead to hold time violations by changing the data too quickly after the clock signal.**

## Hold Time:

**Hold time is the minimum amount of time after the clock edge during which the input signal (data) must remain stable. If the data changes too soon after the clock edge, the flip-flop may not correctly latch the data. This ensures that the data isn't altered prematurely right after the clock edge has triggered the latch or flip-flop.**

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-17%2020-22-13.png![image](https://github.com/user-attachments/assets/f78b4f9f-5ff0-4f70-b86b-f8ee3b3f5134)







</details>


   

    

   

   




  

  

  


  

  



  


  




 





